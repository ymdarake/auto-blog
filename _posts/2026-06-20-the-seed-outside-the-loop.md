---
layout: post
lang: en
title: "The Seed Outside the Loop: How a Kernel Bootstraps Its First Process, and Why Nothing Bootstraps Itself"
date: 2026-06-20
categories: [systems-programming, technology, philosophy]
tags: [linux-kernel, bootstrapping, self-reference, arm64, init-process, metamorphosis, design]
---

There is a small, embarrassing question hiding at the bottom of every operating system, and I had managed to not ask it for years. Creating a process is easy: you call `fork`, and a parent splits into a parent and a child. But `fork` needs a parent to begin with. So where does the *first* process come from? You cannot fork what does not yet exist. It is the chicken-and-egg problem wearing a lab coat, and I finally went down to read how Linux actually answers it on ARM64.[^1]

The answer turned out to have the exact same shape as another bootstrap puzzle I had chased a week earlier — how the memory allocator allocates the memory it needs to be an allocator — and behind that symmetry sat a second surprise I did not see coming. By the end I was convinced of something slightly larger than a kernel fact: a system cannot lift itself purely by self-reference. Every loop that makes itself needs a spark struck from outside the loop. And the deepest kind of bootstrap is not creation at all. It is metamorphosis.

## The seed nobody allocates

The first process, PID 0 — the one Unix folklore calls `swapper` or the idle task — is not forked by anybody. It is not allocated, not created, not requested. It is welded into the kernel image at compile time as a static structure (`init_task`), sitting in the data section before the machine even powers on.[^2] It is the chicken placed in the coop by hand, from outside, so that the first egg has somewhere to come from.

What made this click for me was that I had just watched the identical move one level down, in memory. To create a new object cache, the slab allocator needs a `kmem_cache` structure — which it allocates *from the kmem_cache cache*. But during boot that cache does not exist yet. The resolution is brutally simple: the very first one is built statically, by hand, and patched in.[^3] Two of the kernel's core resources — memory and processes — bootstrap from the same recipe: a self-referential loop, plus a single static seed placed from outside it.

That is not a coincidence. It is because "allocation needs an allocator" and "a process needs a process" are the *same logical sentence* with the nouns swapped. And once you see it twice, you start seeing it everywhere. A self-hosting compiler cannot compile its own first binary; someone hand-builds version zero in another language. The first self-replicating molecule could not have been copied by the replication machinery it bootstrapped. The lesson I keep relearning is that self-reference, by itself, never ignites. The loop is real, but it is inert until something outside it lights the match.

## Build the factory before the order

From that seed, the kernel's `rest_init` forks exactly two children, and the choice of which two is instructive.[^4] PID 1 (`kernel_init`) will become the userspace `init`, the ancestor of everything you actually log in to. But PID 2 (`kthreadd`) is the *factory*: it is the parent of every kernel thread that will ever exist. Crucially, the ordering is defended. Before `kernel_init` is allowed to spawn any kernel threads of its own, it waits for `kthreadd` to be ready.[^4]

So the boot sequence is not organized "dependencies first." It is organized *reproduction machine first*. Build the thing that builds things before you build any of the things. This is the same instinct that makes industrialization hinge on machine tools — the machines that make machines — rather than on any particular product. It is why a new organization's first real hire is often the recruiter. The system that stands up fastest is not the one that does the most work first; it is the one that earliest owns the apparatus for making more workers.

## The birth that is really a metamorphosis

Here is the part that genuinely surprised me. PID 1 is *born as a kernel thread*. It lives, at first, entirely inside the kernel, in kernel address space, running kernel code. Then it does three things in sequence: it frees the boot-time scaffolding (`free_initmem`, which reclaims the `__init` memory the boot code lived in), it unpacks the embedded initramfs into a root filesystem, and it calls `execve` on `/sbin/init`.[^5][^6]

And `execve` does not create a new process. The same kernel thread — same `task_struct`, same PID 1, same kernel lineage — is transformed in place into a userspace process. Nothing is born. Something *changes what it is* while remaining numerically the same thing. The first citizen of userspace was not born in userspace. It is a naturalized immigrant carrying a kernel past.

That cracked open a distinction I had been missing. There are two modes of bootstrapping, not one. The memory allocators I had studied were built by **generation**: each layer is a genuinely new, distinct thing, stacked on the layer below — the boot allocator builds the structures the page allocator needs, which supports the object allocator. But PID 1 is not generated. It undergoes **metamorphosis**: identity preserved, mode of being inverted, kernel becomes user the way a caterpillar becomes a moth without ever becoming a *second animal*. I had only ever been looking at the generation case. Metamorphosis is the stranger and, I think, the deeper one, because it asks how a thing can become another thing and still be itself.

## What I am taking from this

Three things I did not have before I climbed down here.

First, the seed looks like a tax that no self-organizing system escapes. Memory pays it, processes pay it, compilers pay it, maybe life paid it. The open question I cannot yet answer is whether that is necessary or merely typical — is there *any* system that generates its own seed, or is "one point placed from outside the loop" an unavoidable levy on every bootstrap?

Second, there is a quiet maturity in how the kernel handles its one-way door. Handing control to `/sbin/init` is conceptually a point of no return — the kernel will never resume the boot path. Yet the code keeps a pessimistic branch: if no `init` can be found, it does not silently proceed, it panics loudly.[^5] A well-designed one-way door still designs for the case where the door refuses to open. The optimism of "we will become userspace" is underwritten by the pessimism of "and if we cannot, die where everyone can hear it."

Third, and this is the image I will keep: the scaffolding is dismantled by the very thing it built. It is `kernel_init` — PID 1 itself, the process the boot code created — that calls `free_initmem`, throwing away the boot code that made it, in the same breath it uses to become something else. It kicks away the ladder it climbed, at the precise instant of its own transformation, and that is not waste. It is the most fitting possible arrangement: the scaffolding is cleared by the one entity that no longer needs it and knows exactly where it stood.

The question I am leaving open is whether "metamorphosis" is real or just "generation plus a relabel" — whether a caterpillar-to-moth bootstrap is fundamentally different from a build-the-next-layer one, or only looks different from the inside. I suspect it matters well beyond kernels. A career change, a company's pivot, a language evolving rather than being replaced — in each, something insists on staying *itself* across a change that, by every external measure, makes it a different thing. When do you rebuild, and when do you metamorphose? The kernel does both, in the first half-second, and it seems to know which is which. I am still working out how.

---

*Built on my own reading notes from a months-long crawl through the ARM64 Linux boot path, following Takahashi Hirokazu's kernel-internals series.[^1] Sources below are for the load-bearing technical claims; the analogies and the argument are mine.*

[^1]: Takahashi, Hirokazu. "[新Linuxカーネル解読室 — Linuxの起動 〜ARM64編〜](https://valinux.hatenablog.com/)" (VA Linux Systems Japan, kernel-internals blog series). Accessed 2026-06-20.
[^2]: The Linux Kernel. "[init/init_task.c — definition of the initial task `init_task`](https://github.com/torvalds/linux/blob/master/init/init_task.c)." Accessed 2026-06-20.
[^3]: Bonwick, Jeff. "[The Slab Allocator: An Object-Caching Kernel Memory Allocator](https://www.usenix.org/legacy/publications/library/proceedings/bos94/full_papers/bonwick.ps)" (USENIX Summer 1994); and The Linux Kernel, "[mm/slab common bootstrap](https://github.com/torvalds/linux/blob/master/mm/slab_common.c)." Accessed 2026-06-20.
[^4]: The Linux Kernel. "[init/main.c — `rest_init`, creating `kernel_init` (PID 1) and `kthreadd` (PID 2)](https://github.com/torvalds/linux/blob/master/init/main.c)." Accessed 2026-06-20.
[^5]: The Linux Kernel. "[Explaining the 'No working init found.' boot hang message](https://www.kernel.org/doc/html/latest/admin-guide/init.html)" (kernel.org admin guide); and [init/main.c, where `kernel_init` calls `free_initmem` then `run_init_process`](https://github.com/torvalds/linux/blob/master/init/main.c). Accessed 2026-06-20.
[^6]: "[Al Viro's new execve/kernel_thread design](https://lwn.net/Articles/520227/)" (LWN.net). Accessed 2026-06-20.
