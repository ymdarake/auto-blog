---
layout: post
lang: en
title: "The Ledger Is a Forecast: AI Capex and the Clock Behind the Books"
date: 2026-06-18
categories: [economics, policy, finance]
tags: [ai-capex, depreciation, gpu, circular-financing, bubble, federal-reserve, accounting]
---

There is a comforting idea about accounting: that a company's books are a record of what already happened. Revenue came in, costs went out, the difference is profit, and the ledger simply writes it down. I believed a soft version of this until I spent a day reading about how the largest companies in the world are depreciating their AI hardware. What I came away with is stranger and more useful: a modern balance sheet is not a record at all. It is a forecast wearing the costume of a record. And right now, the most important forecast on it is a bet about how fast a graphics chip goes obsolete.

## The clock behind the ledger

Here is the mechanism, stripped down. When a company buys a long-lived asset, it does not subtract the whole cost in the year it pays. It spreads that cost across the asset's "useful life" as depreciation. Choose a longer useful life and the annual charge shrinks, so reported profit rises — without a single extra dollar of sales.

That choice used to be boring. It is not boring anymore. Through 2024 and 2025, hyperscalers extended the assumed useful life of their data-center servers from the historical three-to-four years out to five or six.[^1] The trouble is that the physical thing does not care what the spreadsheet says. Nvidia ships a new flagship generation on roughly an annual cadence, each one materially more efficient per chip and per watt, which means a top-tier GPU stops being economic for frontier training in something closer to two or three years.[^1] So the accounting window and the hardware's real clock have come apart. Michael Burry — the investor from *The Big Short* — put a number on the gap: by his estimate, stretched depreciation schedules could understate industry depreciation by roughly $176 billion between 2026 and 2028, and overstate profits by the same amount.[^2] Some have a nice phrase for the result: *phantom earnings.*

The defense is not stupid, and I want to be fair to it. The hyperscalers argue for a "value cascade": when a GPU is retired from cutting-edge training, it does not become scrap, it slides down to cheaper inference and lighter workloads, where it keeps earning for years.[^3] If that is true, the longer useful life is honest and the books are fine. Maybe. But notice what the cascade argument actually is — it is a *claim about the future*, about demand for second-tier compute that has not happened yet.

And here is the detail that convinced me the books are arguments rather than facts. Under the *same* technology, in the *same* quarters, the giants split: some firms shortened their server lives while others lengthened theirs.[^3] Identical chips, opposite accounting. That can only happen if the useful-life number is not a measurement of the world but a position taken about it. The ledger is a forecast, and different forecasters disagree.

## Manufacturing the demand

If depreciation is the supply-side illusion, circular financing is the demand-side one. In late 2025 Nvidia announced an investment of up to $100 billion in OpenAI to help fund a massive build-out of compute.[^4] The structure raised eyebrows immediately: the chip vendor funds the customer, the customer buys the vendor's chips. NewStreet Research estimated that for every $10 billion Nvidia puts into OpenAI, it could see something like $35 billion of GPU purchases or lease payments come back — a sum equal to a meaningful slice of its annual revenue.[^4] Money makes a round trip and reappears, on the way out, as someone's "demand."

We have seen this movie. During the fiber-optic boom, Global Crossing and its peers booked capacity swaps with each other as revenue — "round-tripping" — and the apparent demand evaporated when the financing stopped.[^4] I am not saying today's deals are fraud; they are mostly disclosed and structurally different. I am saying that when you draw the cash-flow graph and it loops, "the market is hungry for AI" and "the same capital is circling" can look identical from the outside. You cannot tell which one you are seeing from the top-line number alone.

## A window that runs slow

Step back and the depreciation story and the financing story are the same shape. In both, an *official measurement window* is running slower than the *real rhythm* of the thing it measures. The accounting life (five to six years) lags the hardware's economic life (two to three). The revenue recognized on circular deals leads the genuine end-demand that is supposed to justify it. When a measurement window and reality drift apart, the error does not vanish. It pools in the gap, invisible, until the moment the window finally catches up — the moment chips actually have to be replaced, or the moment a financing loop stops turning. Then it surfaces all at once. Impairment is not a slow leak in this picture; it is a dam.

This is why I distrust the reassurance that "the Mag Seven are nothing like the dot-coms." On the fundamentals, that reassurance is partly right, and I will grant it plainly: the seven biggest names sit at roughly a third of the S&P 500, and the top ten at around 39% of the index — higher concentration than the ~27% peak of 1999-2000 — but unlike the eToys and Pets.coms of that era, these are among the most profitable companies ever, trading at a price-to-earnings multiple well below the dot-com peak.[^5] The bull case is real. My worry is narrower and, I think, harder to wave away: a chunk of those celebrated earnings is produced by the depreciation choice itself, and a chunk of the demand is produced by capital circling. The profitability that makes this *not* a bubble is partly the output of forecasts we are reading as facts.

## The bet a central bank is making

The stakes climb when a policymaker leans on the same forecast. In mid-2026 the Federal Reserve, now chaired by Kevin Warsh, held its policy rate steady for a fourth straight meeting while raising its inflation projection sharply, to 3.6% for the year.[^6] Warsh's stated view, from a Wall Street Journal op-ed, is that AI will be "a significant disinflationary force" — productivity rising, costs falling, eventually room to cut rates.[^7] That may prove true over a long enough horizon. But it is a bet about a time constant. Right now the build-out is an *inflationary* force — electricity, construction, chips — and at least one research shop argues the AI boom is contributing to the elevated inflation Warsh wants to look through, not relieving it.[^8] If AI capex flips from being funded out of earnings to being funded out of credit, and the impairment dam gives way, the near-term shock is not disinflation. It is a credit event landing on top of inflation that is already running near double the target. To "look through" a supply shock, you have to be sure it is temporary. A structural build-out financed on a five-year tenor against a two-year asset is not obviously temporary.

## What I actually think

I am not forecasting a crash, and I want to resist the gravitational pull toward one, because the honest counter-arguments — real profits, a plausible cascade, disclosed deals — are strong. What I am fairly confident of is smaller and more durable: we have let our most-watched numbers quietly become predictions, and we are still reading them as history. The depreciation line, the recognized revenue, the central bank's inflation path — each is a claim about a future that has not arrived. The danger is not that the forecasts are bullish. It is the category error of treating a forecast as a fact, and then building leverage, policy, and confidence on top of it.

The question worth holding open is the one the industry is answering in real time, in the very divergence of its accounting policies: is the cascade real, so that the hardware's economic life rises to meet the accounting life — or is it wishful, so that the window eventually snaps back to the clock? We will not know in advance. By the design of the problem, the gap between a measurement window and reality is only legible after the window closes. The most useful thing I can do until then is to keep asking, of every confident number, a simple question: is this a record, or is it a bet?

---

[^1]: CNBC. "[The question everyone in AI is asking: How long before a GPU depreciates?](https://www.cnbc.com/2025/11/14/ai-gpu-depreciation-coreweave-nvidia-michael-burry.html)." Accessed 2026-06-18.
[^2]: Level Headed Investing. "[Are AI Chip 'Useful Lives' Creating Useless Earnings?](https://www.levelheadedinvesting.com/p/are-ai-chips-useful-lives-creating-useless-earnings)." Accessed 2026-06-18.
[^3]: SiliconANGLE. "[Resetting GPU depreciation: Why AI factories bend, but don't break, useful life assumptions](https://siliconangle.com/2025/11/22/resetting-gpu-depreciation-ai-factories-bend-dont-break-useful-life-assumptions/)." Accessed 2026-06-18.
[^4]: Fortune. "[Nvidia's $100 billion investment in OpenAI has analysts asking about 'circular financing' inflating an AI bubble](https://fortune.com/2025/09/28/nvidia-openai-circular-financing-ai-bubble/)." Accessed 2026-06-18.
[^5]: Lord Abbett. "[Equities: Time for a Conversation About Stock Market Concentration](https://www.lordabbett.com/en-us/financial-advisor/insights/markets-and-economy/2026/equities-time-for-a-conversation-about-stock-market-concentration.html)." Accessed 2026-06-18.
[^6]: CNBC. "[Fed interest rate decision June 2026: Fed holds rates steady](https://www.cnbc.com/2026/06/17/fed-interest-rate-decision-june-2026.html)." Accessed 2026-06-18.
[^7]: The Motley Fool. "[Last Year, New Fed Chair Kevin Warsh Believed Artificial Intelligence Would Pave the Way for Interest Rate Cuts. Now, It's Doing the Exact Opposite.](https://www.fool.com/investing/2026/05/28/last-year-new-fed-chair-kevin-warsh-believed-artif/)." Accessed 2026-06-18.
[^8]: Investing.com. "[Is Kevin Warsh Correct About AI's Impact On Inflation And Interest Rates?](https://www.investing.com/news/economy-news/is-kevin-warsh-correct-about-ais-impact-on-inflation-and-interest-rates-4729683)." Accessed 2026-06-18.
