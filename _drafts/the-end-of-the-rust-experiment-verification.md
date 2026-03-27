# Verification Report: The End of the Rust Experiment

Date: 2026-03-27

## Source Traceability

| Claim | Source Type | Source |
|-------|-----------|-------|
| Rust no longer experimental, decided at 2025 Kernel Maintainer Summit in Tokyo | external | devclass.com [^1] |
| "Zero pushback" at summit | external | devclass.com [^1] |
| Greg Kroah-Hartman: Rust drivers proving safer than C | external | devclass.com [^1] |
| Microsoft: ~70% of CVEs from memory safety issues | external | MSRC blog [^2] |
| Android 16 / 6.12 kernel ships ashmem in Rust | external | rust-for-linux.com [^3] |
| Nova GPU driver merged in Linux 6.15, May 2025 | external | Phoronix [^4] |
| Nova targets NVIDIA Turing+ GPUs, successor to Nouveau | external | Phoronix [^4] |
| Nova still in early stages of development | external | Phoronix [^4], It's FOSS |
| Debian requires Rust for APT from May 2026 | external | LWN.net [^5] |
| Conservative community paradigm shift pattern analysis | opinion | (author's analysis) |
| Moral responsibility of infrastructure maintenance | opinion | (author's analysis) |

## Fact-Check Results

| # | Claim | Search Query | Result | Action |
|---|-------|-------------|--------|--------|
| F1 | Rust permanent at 2025 Kernel Maintainer Summit Tokyo | "Rust Linux kernel permanent adoption 2025 Kernel Maintainer Summit" | Verified | Multiple sources confirm (devclass, LWN, Phoronix, Gigazine) |
| F2 | Microsoft ~70% CVEs from memory safety | "Microsoft 70% security vulnerabilities memory safety issues MSRC" | Verified | MSRC blog (2019), widely cited. Matt Miller presentation at BlueHat IL |
| F3 | Android 16 / ashmem in Rust on 6.12 kernel | "Android ashmem Rust kernel driver 2025 2026" | Verified | rust-for-linux.com, devclass confirm |
| F4 | Nova merged in Linux 6.15, May 2025 | "Nova GPU driver Rust Linux kernel merged 2025" | Verified | Phoronix, It's FOSS, kernel docs confirm. Clarified as bare-bones/early stage |
| F5 | Debian Rust requirement for APT from May 2026 | "Debian Rust requirement APT 2026" | Verified | LWN, The Register, Phoronix, NotebookCheck all confirm |

### Removed from previous draft (Contradicted / Unverified)

| Claim | Issue | Action |
|-------|-------|--------|
| "60万行の Rust コードが kernel に存在" (JP version) | Contradicted: actual count ~25K lines as of April 2025 | Removed from article |
| "ウォータールー大学の研究で67%が防止可能" (JP version) | Unverified: could not find this study | Removed; replaced with verified Microsoft 70% stat |
| "3,108 CVEs in 2024, 79% increase" (EN version) | Unverified in this round (single source: TuxCare) | Removed; not essential to argument |
| "38% of kernel CVEs from memory management/networking" (EN version) | Unverified in this round | Removed; replaced with broader verified claim |

## Copyright Review

- Direct quotes: 1 ("zero pushback" — 2 words, attributed to source [^1])
- Paraphrased content: 5 instances (all with source attribution via footnotes)
- Original analysis: ~60% of article (conservative dilemma, ethics of infrastructure, ripple effects)
- No continuous 7+ word sequences copied from any source

## Overall Assessment

- Fact-check pass rate: 5/5 Verified (100%)
- Contradicted claims from previous draft: 2 (removed)
- Unverified claims from previous draft: 2 (removed)
- Copyright risk: Low
- Single-source concentration: No source exceeds 10% of article content
- Ready for review: Yes
