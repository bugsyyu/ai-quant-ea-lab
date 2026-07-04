# Financial EA, Traditional Quant, and AI-Driven Quantitative Trading Systems

## Market Research & Comparison Report

**Prepared:** July 4, 2026
**Purpose:** Pre-build market research for a founder evaluating entry into the financial EA (Expert Advisor) / quantitative trading product space.
**Audience:** Technically capable founder / product builder.
**Language versions:** English (this document) · [中文版](market-research-ea-quant-ai-trading-2026.zh-CN.md). Both versions carry identical data and conclusions; the English version and its cited primary sources govern in case of discrepancy.

> **DISCLAIMER (read first).** This report is for **market research and product analysis only**. It does **not** constitute investment advice, an offer or solicitation of any financial product, or a recommendation to trade. **No trading system — rule-based, AI-driven, or manual — can guarantee profits.** All performance figures cited here are historical, frequently unaudited, and in many cases explicitly promotional; past performance does not predict future results. Figures labeled "promotional" should be treated as *from promotional material and not necessarily equivalent to reproducible real-world performance*. See §12 for the full disclaimer.

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Methodology and Source-Credibility Framework](#2-methodology-and-source-credibility-framework)
3. [Market Landscape: Representative Products and Platforms](#3-market-landscape-representative-products-and-platforms)
4. [Traditional Rule-Based Quant: Advantages and Limitations](#4-traditional-rule-based-quant-advantages-and-limitations)
5. [AI/ML-Driven Quant: What It Adds, What It Risks](#5-aiml-driven-quant-what-it-adds-what-it-risks)
6. [Three-Way Comparison: Traditional Quant vs AI Quant vs Manual Trading](#6-three-way-comparison-traditional-quant-vs-ai-quant-vs-manual-trading)
7. [Public Performance Data and Case Studies](#7-public-performance-data-and-case-studies)
8. [EA Deep Dive: The MT4/MT5 Ecosystem](#8-ea-deep-dive-the-mt4mt5-ecosystem)
9. [Product Opportunity Analysis](#9-product-opportunity-analysis)
10. [Conclusions and Recommendations](#10-conclusions-and-recommendations)
11. [References](#11-references)
12. [Full Disclaimer](#12-full-disclaimer)

---

## 1. Executive Summary

**The market is large, mature in infrastructure, and systematically dishonest in retail marketing.** Three findings frame everything else in this report:

1. **Execution automation is a solved problem; alpha is not.** The infrastructure layer — MetaTrader 4/5, cTrader, crypto exchange APIs, QuantConnect-style research platforms — is mature, cheap, and commoditized. A retail trader can deploy an automated strategy for under $100. What remains genuinely hard, for both rule-based and AI systems, is producing a *durable, positive expected return after costs*, and — critically for a product builder — *proving it honestly*. Peer-reviewed work shows that standard backtest workflows produce false positives almost by construction: with only 5 years of data, trying more than ~45 strategy configurations makes it nearly certain you will find a strategy with an in-sample Sharpe ratio of 1.0 and an *expected out-of-sample Sharpe of zero* (Bailey, Borwein, López de Prado & Zhu, *Notices of the AMS*, May 2014 — peer-reviewed; high credibility).

2. **AI adds demonstrated research value and unproven live-trading value.** The best academic evidence (Gu, Kelly & Xiu, *Review of Financial Studies*, 2020 — adversarially verified against the published text during this research) shows machine learning roughly **doubling** the out-of-sample Sharpe ratio of linear benchmark strategies on US equities (1.35 vs 0.61 value-weighted). But follow-up work (Avramov, Cheng & Metzker, *Management Science*, 2023) shows those gains concentrate in microcaps and shrink sharply after trading costs; a 2025 study of LLM trading agents ("Profit Mirage," arXiv, Oct 2025) found **Sharpe ratios decay 51–62% once the test period moves past the model's training cutoff** — i.e., much of the advertised LLM-agent performance is information leakage, not skill. At the fund level, the Eurekahedge AI Hedge Fund Index annualized **9.8% from Dec 2009 to Jul 2024 versus 13.7% for the S&P 500** (index data via IG/With Intelligence, Nov 2024 — medium credibility). "AI beats the market" is, as of 2026, a marketing claim, not an established fact.

3. **The retail EA/bot market's core dysfunction — and therefore its product opportunity — is trust and risk control, not strategy supply.** There are ~10,000–14,000 products on the MQL5 Market alone (MetaQuotes marketing/company article; medium credibility). Regulators on both sides of the Atlantic issued 2024 alerts specifically about AI-trading-bot fraud (CFTC; SEC/NASAA/FINRA — both Jan 25, 2024; primary sources). The mandated European disclosure environment shows **74–89% of retail CFD accounts lose money** (ESMA, 2018; primary source). Meanwhile the fastest-growing adjacent segment — prop-firm challenges (FTMO: **$203.9M revenue in 2023**, TradeInformer analysis of company filings; medium-high credibility) — monetizes precisely the thing retail traders lack: enforced risk discipline. The credible product gaps are therefore in **verification, risk management, and honest validation tooling**, not in yet another strategy-in-a-box.

**Bottom-line orientation for a builder:** Traditional rule-based quant's real advantages (discipline, speed, repeatability, testability, multi-market scale) are proven and commoditized. AI quant's real advantages (nonlinear pattern extraction, text/news processing, research acceleration) are real but mostly *upstream* — in research, screening, and monitoring — while end-to-end AI live trading remains unstable and partially fraudulent in retail marketing. The EA market has huge distribution (MT4/MT5) and a documented integrity problem. The strongest opportunities identified in §9 are (a) a **risk-control-first EA / equity-protection layer** (with prop-firm traders as a beachhead market), and (b) an **anti-overfitting strategy-validation platform** that brings institutional validation methods (CPCV, PBO, deflated Sharpe) plus AI-assisted research to serious retail/semi-pro builders — with a **signal-selling platform being the least attractive** direction on compliance and trust grounds.

---

## 2. Methodology and Source-Credibility Framework

### 2.1 How this research was produced

- A multi-agent research pipeline decomposed the question into five evidence angles (product landscape/pricing; institutional performance benchmarks; peer-reviewed evidence on ML in trading; regulatory warnings and mandated loss-rate disclosures; practitioner EA failure modes), ran parallel web searches per angle, fetched the most relevant primary and secondary sources, and extracted quotable claims.
- A subset of claims went through **adversarial verification** (independent agents attempting to refute each claim against primary text). Claims that survived 3-0 verification are marked **[verified]**. Where verification was interrupted (a session limit during the run), claims are instead labeled with their source tier below; none were fabricated, and direct quotes were only used where recovered from the source or from consistent search-index snapshots of it.
- Several key pages (mql5.com blog posts, arxiv.org abstract pages, quantconnect.com/pricing) block automated fetching (HTTP 403). Where content was reconstructed from search-engine snippets or secondary summaries, this is explicitly noted, and confidence is reduced accordingly.

### 2.2 Credibility tiers used throughout

| Tier | Label | What it means | Examples in this report |
|---|---|---|---|
| 1 | **High (primary/peer-reviewed)** | Regulator publications; peer-reviewed journals | ESMA, FCA, CFTC, SEC/NASAA/FINRA; *Review of Financial Studies*, *Management Science*, *Journal of Computational Finance*, *Notices of the AMS*, *Knowledge-Based Systems* |
| 2 | **Medium (established secondary)** | Industry press with editorial standards; index providers; company-filing analyses; arXiv preprints (methodical but not peer-reviewed) | Hedgeweek, Finance Magnates, TradeInformer, SG/BarclayHedge/Eurekahedge index data, CFM/arXiv papers |
| 3 | **Low (promotional/uncontrolled)** | Vendor sites and blogs, affiliate review sites, community estimates | MQL5 vendor blogs, bot-review sites, "best trading robots" listicles, all advertised win rates and returns |

**Rules applied:** every load-bearing number carries a source, date, and tier; Tier-3 performance numbers are always labeled *promotional*; where no reliable number exists, the report says **"data missing"** rather than inventing one.

---

## 3. Market Landscape: Representative Products and Platforms

### 3.1 Category map

The "quant product" market is really six distinct markets with different users, price points, and trust mechanics:

1. **Retail EAs (forex/gold/indices, MT4/MT5)** — packaged strategies sold as software licenses.
2. **Crypto trading bots (cloud SaaS)** — grid/DCA/signal bots connected to exchange APIs.
3. **Retail quant research & algo platforms** — code-first backtesting/live-trading infrastructure.
4. **AI stock-picking / analytics tools** — screening, scoring, and signal research (usually not auto-executing).
5. **Institutional systematic strategies (CTAs, quant hedge funds)** — the professional benchmark for what systematic trading actually returns.
6. **Adjacent monetization layers** — copy trading, signal marketplaces, prop-firm challenges: where retail demand actually pays today.

### 3.2 Representative product comparison table

> Pricing retrieved June–July 2026 unless noted; prices change frequently — treat as indicative. Performance columns are deliberately sparse: **almost no retail product publishes independently verifiable live performance** (see §7.5). "Promo" = from promotional material and not necessarily equivalent to reproducible real-world performance.

| Product / Platform | Category | Target users | Pricing (source, tier) | Advertised edge | Publicly verifiable performance? |
|---|---|---|---|---|---|
| **MQL5 Market EAs** (aggregate: thousands of forex/gold EAs) | Retail EA store (MT4/MT5) | Retail forex/CFD traders | Typically **$30–$2,000+ per license**; ~14,000 products total, ~4,800 robots; ~6,000 rentable, ~3,800 free (MetaQuotes article & market pages; Tier 2/3) | "Set-and-forget" automation; backtest screenshots; AI branding increasingly common | **No.** Market rankings reflect sales/popularity, not verified profit (vendor-community blog, Tier 3); optional signal accounts exist but are self-selected |
| **Pionex** | Crypto bot (exchange-integrated) | Crypto retail beginners | **16 built-in bots free; ~0.05% trading fee** (vendor + comparison sites, Tier 3) | Free grid/DCA bots; low barrier | No audited aggregate user P&L published — **data missing** |
| **3Commas** | Crypto bot SaaS | Crypto retail/semi-pro | ~**$29–$99/mo** across tiers (2025–26; ~30–40% off annually; free paper trading) (vendor + reviews, Tier 3) | Multi-exchange terminal (18+ exchanges), DCA/grid/signal bots, copy features | No; historic marketing cites e.g. "5–20% monthly returns" in third-party bot roundups — **promo, red-flag range** |
| **Cryptohopper** | Crypto bot SaaS | Crypto retail | **$0–~$107.50/mo** (Hero tier ~$99–107.50) (vendor + reviews, Tier 3) | No-code strategy designer, marketplace of signals/strategies | No — **data missing** |
| **QuantConnect (LEAN)** | Code-first quant platform | Programmers, semi-pro/pro quants | Free tier; **Team $24/user/mo; Trading Firm $48/user/mo**; backtest nodes ~$14–96/mo; live nodes ~$24–1,000/mo (docs/reviews, Tier 2/3) | Institutional-grade multi-asset backtesting (equities, futures, FX, crypto, options), open-source engine, broker integrations | Platform doesn't claim returns (infrastructure, not signals) — the honest model |
| **Trade Ideas ("Holly" AI)** | AI stock scanner/signals | Active US equity day traders | From ~**$118/mo** (third-party 2026 roundup, Tier 3) | AI scanning; advertised "Holly" stats such as "63.4% average annual return" | **Promo only** — simulated/vendor-reported; no independent audit found — treat as marketing |
| **TrendSpider** | Charting + no-code automation | Technical-analysis retail | From ~**$39/mo** (third-party 2026 roundup, Tier 3) | Automated TA, pattern recognition, strategy tester | No — **data missing** |
| **Composer (now "Composer by SoFi")** | No-code strategy marketplace + brokerage | US retail investors | ~**$32/mo** (site/reviews, Tier 3) | Drag-and-drop "symphonies," community strategies, AI copilot | Backtests shown in-app; live community results not independently audited — **data missing** |
| **Danelfin** | AI stock scoring | Retail stock pickers | ~**$17–49/mo** (vendor pricing pages, Tier 3) | "AI Score" ranking stocks by probability of beating market | Vendor publishes hit-rate claims — **promo**; no independent audit found |
| **Tickeron** | AI signals/bots (stocks, ETFs, crypto, FX) | Retail | ~**$60–250/mo** by tier (vendor/reviews, Tier 3) | "AI robots," pattern engines | **Promo only**; no independent audit found |
| **StrategyQuant X** | EA/strategy generator (genetic search) | EA builders, semi-pro | One-time license, several hundred to ~$2,000 depending on edition (vendor; price not re-verified this session — Tier 3, approximate) | Mass-generates and stress-tests strategies, exports MQL/other code | No — and note: automated mass-search is exactly the overfitting machine §8.4 warns about unless validation is rigorous |
| **NinjaTrader / cTrader / TradingView ecosystems** | Alternative runtime platforms | Futures (NT), FX/CFD (cT), everything (TV) | NT: free platform w/ funded brokerage, paid license options; cTrader: free to traders (broker-funded); TradingView: freemium subscriptions (general industry knowledge — Tier 3, verify current pricing) | C#/cBots/Pine Script automation; TV has the largest social/charting user base | No platform-level performance claims (infrastructure) |
| **Hummingbot** | Open-source market-making/arbitrage bot framework | Technical crypto users, market makers | Open source (free); optional paid cloud/miner programs (general knowledge — Tier 3) | Exchange market-making, cross-exchange arbitrage | No aggregate audited results — **data missing** |
| **SG CTA / SG Trend Index constituents** (e.g., largest institutional CTAs) | Institutional systematic futures (CTA) | Institutions, allocators | 2/20-style management+performance fees (varies by fund) | Diversified trend/managed futures; crisis alpha | **Yes — daily index data** (SG Prime Services; Tier 2). See §7.1 |
| **Quant hedge funds** (Renaissance, Two Sigma, AQR, Winton, CFM, Marshall Wace) | Institutional AI/stat-arb/multi-strategy | Institutions (mostly closed/qualified investors) | High fees (Medallion historically 5% + 44% perf. — Zuckerman estimates, Tier 2) | Massive data + infrastructure + talent moat | Partially — via press (Tier 2), not public audit. See §7.1 |
| **FTMO** (prop-firm challenge, adjacent segment) | Funded-trader evaluations | Retail traders seeking capital | Challenge fees (~€89–1,080 by account size — vendor, Tier 3); **2023 revenue $203.9M** (TradeInformer analysis of filings, Tier 2) | Trade "firm capital" after passing a risk-rule exam; 80–90% profit splits | Payout stats partially disclosed: **$75.2M paid out in 2023; >$300k/day in early 2024** (company statements via Tier 2/3 sources); industry-average challenge pass rate ~14%, ~7% ever get a payout (FPFX data via TradeInformer, Tier 2) |

### 3.3 Reading the landscape by category

**Forex/gold EAs (retail).** Distribution is centralized on the MQL5 Market (MT4/MT5's official store). MetaQuotes' own materials describe ~14,000 products (≈4,800 trading robots), with prices from free to $2,000+; the platform advertises "a choice among 10,000 products" today (MetaQuotes article "14,000 trading robots in the MetaTrader Market" and metatrader5.com marketing — Tier 2 for scale, undated precisely; treat counts as order-of-magnitude). Gold (XAUUSD) EAs are a marketing subgenre of their own because gold's volatility makes backtests look spectacular — and makes live execution costs (spread spikes to ~8 pips at the New York open, 30+ pip slippage around news, per an MQL5 practitioner post, Apr 2026 — Tier 3, snippet-recovered) far worse than simulated. **The category's defining feature is unverifiable performance claims at scale** (see §7.4, §8).

**Crypto bots.** The freemium leaders (Pionex free-with-spread; 3Commas/Cryptohopper SaaS at ~$0–110/mo) sell *convenience automation* — grid and DCA bots that are mechanically simple and honestly useful for order discipline, but which embed a short-volatility/averaging-down risk profile that users routinely mistake for alpha. Marketing in this category routinely implies monthly returns ("5–20% monthly" appears in third-party bot marketing roundups — **promo; treat as a red flag**: the CFTC's Jan 2024 advisory explicitly calls guaranteed/high-return bot claims a fraud marker; Tier 1).

**Stock quant platforms.** QuantConnect is the credibility benchmark: it sells infrastructure (multi-asset backtesting + live deployment) rather than returns, priced like a developer tool ($24–48/user/mo tiers + compute nodes). This is the honest end of the market and also the most defensible business model pattern observed (see §9). Trade Ideas / Tickeron / Danelfin sell AI-labeled *signals/scores* with vendor-reported performance — uniformly unaudited (**promo**).

**Futures/CTA-style systems.** For institutional-grade evidence of what disciplined rule-based trading actually earns, CTA indices are the best public data: mid-single-digit long-run CAGR with ~20% max drawdowns (§7.1) — dramatically lower than retail EA marketing, and the single most useful calibration anchor a builder can internalize.

**Grid/arbitrage/trend/mean-reversion/multi-factor.** These are *strategy archetypes*, not products, and appear across all categories: grid/martingale dominate retail EA sales (high win rate optics; tail risk — §8.3); trend-following dominates institutional CTAs (positive skew, long droughts); true arbitrage (latency, triangular, cross-exchange) is capacity-constrained and infrastructure-intensive (retail products claiming "arbitrage" usually aren't); multi-factor equity lives on platforms (QuantConnect; WorldQuant's crowdsourced BRAIN platform — general knowledge, Tier 3) rather than in boxed products.

**Retail vs institutional divide.** Institutions buy research infrastructure, data, and execution; returns come from proprietary strategies they never sell. Retail is sold *strategies* precisely because sellers can monetize hope without audited performance. This asymmetry is the single most important structural fact for product design: **the sustainable businesses in this market sell tools, infrastructure, risk control, or verification — not alpha.**

---

## 4. Traditional Rule-Based Quant: Advantages and Limitations

"Traditional quant" here means systems built from explicit rules: indicators, statistical/factor models, historical backtesting, and programmatic execution — the technology behind both retail EAs and institutional CTAs.

### 4.1 Advantages versus manual discretionary trading

| Dimension | Rule-based quant | Manual discretionary | Why it matters |
|---|---|---|---|
| **Discipline & emotional control** | Rules execute regardless of fear/greed; no revenge trading | Documented behavioral failure point; the ESMA/FCA loss-rate environment (74–89% / 62–82% of retail accounts losing) is substantially a behavioral phenomenon | The strongest, least controversial quant advantage |
| **Execution speed & precision** | Milliseconds; exact sizes, stops placed atomically | Seconds–minutes; fat-finger and hesitation risk | Matters most for scalping/news strategies; matters less for daily-bar systems |
| **Backtestability** | Rules can be simulated on history *before* risking money | A discretionary process cannot be faithfully replayed | Double-edged — see §4.2: testability is also how overfitting happens |
| **Repeatability & consistency** | Same inputs → same outputs; auditable | Depends on sleep, mood, attention | Prerequisite for diagnosing what works |
| **Multi-market monitoring & scalability** | One engine can watch 50 pairs 24/5, or 24/7 in crypto | Human attention caps at a few instruments | Automation's most commercially honest selling point |
| **Automated risk control** | Hard stops, exposure caps, margin checks enforced in code | Stops get widened "just this once" | Only real if coded honestly — many EAs code the opposite (martingale) |
| **Strategy standardization** | Version-controlled, transferable, teachable | Tacit knowledge, hard to transfer | Enables products, teams, and audits |

The honest institutional benchmark for these advantages: systematic trend-following CTAs — the purest large-scale expression of rule-based trading — delivered roughly **7.0% CAGR with ~20.8% max drawdown since 2000** (TTU Trend Following composite; SG Trend Index ~4.9% annualized since 2000, 0.95 correlated), versus the S&P 500 total return's **7.7% CAGR with a 50.95% max drawdown** (Top Traders Unplugged monthly report, June-2025 data — Tier 2). Read that carefully: elite rule-based trading's realistic value proposition over 25 years was **similar returns to equities with ~40% of the drawdown**, i.e., *risk shaping* — not the multiplied returns retail EA marketing implies.

### 4.2 Limitations — with the quantitative evidence

1. **Overfitting is the default outcome, not an edge case.** With 5 years of data, testing more than ~45 independent strategy configurations makes it almost guaranteed you'll find one with in-sample Sharpe ≈ 1.0 and **expected out-of-sample Sharpe ≈ 0**; under realistic serial dependence, overfit strategies have **negative** expected out-of-sample returns (Bailey et al., *Notices of the AMS*, May 2014 — Tier 1). The same team formalized the **Probability of Backtest Overfitting (PBO)** and showed the standard hold-out test is "unreliable and inaccurate" for investment backtests (*Journal of Computational Finance*, 2017 — Tier 1; abstract verified against source). An optimizer sweeping 10,000 parameter sets — the default MT5/StrategyQuant workflow — is orders of magnitude past these bounds.
2. **Walk-forward — the retail industry's standard "proof" — is the weakest validator.** A controlled 2024 study found Combinatorial Purged Cross-Validation (CPCV) markedly superior to K-Fold and Walk-Forward at preventing false discoveries; **Walk-Forward performed worst**, with "notable shortcomings in false discovery prevention" (Arian, Norouzi Mobarekeh & Seco, *Knowledge-Based Systems* 305, 2024 — Tier 1).
3. **Historical validity decays.** Across 72 published equity strategies, out-of-sample Sharpe decay is predictable, and **each additional year of publication vintage adds ~5 percentage points of Sharpe decay**; publication year alone explains ~30% of decay variance, with overfitting-related variables adding ~15% (Falck, Rej & Thesmar, CFM / arXiv:2105.01380, May 2021 — Tier 2). Edges rot — a strategy product needs a research treadmill, not a one-time discovery.
4. **Regime vulnerability.** The SG Trend Index — professionally run, diversified, risk-managed — was **down 15.05% over the 12 months to June 2025 with a 20.6% max drawdown** (Tier 2). Rule-based systems encode a regime assumption; when the regime leaves, discipline faithfully executes losses. No retail EA is exempt from what institutional CTAs cannot escape.
5. **Costs, slippage, and data quality flip signs.** Backtests assume executions that live markets don't grant: spreads widen at news/session opens, slippage is asymmetric (adverse fills outnumber favorable ones in fast markets), swap/rollover accrues, and "99% modeling quality" tick data varies by source (MQL5 practitioner posts, 2025–26 — Tier 3, but mechanically uncontroversial and consistent with Tier-1 microstructure literature). A modestly profitable backtest minus real frictions is routinely a live loser (§8.4).
6. **Black swans and gap risk.** Hard stops don't bind across weekend gaps, flash crashes, or de-pegs; any strategy short volatility or averaging into losers (grid/martingale) converts these into account-terminal events (§8.3 case study: a tracked grid/martingale account rode $2,000 → $25,000+ → **$8**; Forex Robot Lab review — Tier 3, single case, illustrative).
7. **Parameter dependency.** Optimized parameters are point estimates from one historical draw. Robustness across neighborhoods of parameter space, instruments, and periods — not peak performance — is the design goal; most sold EAs are tuned to the peak (that's what sells screenshots).

---

## 5. AI/ML-Driven Quant: What It Adds, What It Risks

"AI quant" spans ML/DL forecasting, reinforcement learning, NLP/LLM news & sentiment processing, time-series foundation models, order-flow models, regime detection, and adaptive parameter control.

### 5.1 Demonstrated advantages (evidence-backed)

1. **Nonlinear pattern extraction measurably improves prediction.** Gu, Kelly & Xiu (*RFS*, 2020 — Tier 1; **adversarially verified 3-0 in this research**): neural-net forecasts on ~30,000 US stocks (1957–2016, 94 characteristics + interactions, 900+ signals) produced a long-short decile portfolio with **out-of-sample annualized Sharpe 1.35 value-weighted (2.45 equal-weighted) vs 0.61 (0.83) for OLS**; S&P 500 timing Sharpe improved to 0.77 vs 0.51 buy-and-hold. Gains trace specifically to **nonlinear interactions** among known signal families (momentum, liquidity, volatility) — ML recombines known anomalies better; it did not discover exotic new ones.
   **Mandatory qualification:** Avramov, Cheng & Metzker (*Management Science*, 2023 — Tier 1) show these ML gains concentrate in microcaps/hard-to-arbitrage stocks and **shrink substantially under trading costs and economic restrictions**. Academic Sharpe ≠ deployable Sharpe.
2. **Text/news processing at scale is a real institutional edge.** Hedge funds that systematically bulk-download and analyze 10-K filings from SEC EDGAR earn excess returns relative to peers (Zeng & Zhou, study of 678 hedge funds' EDGAR access logs, 2000–2022, *Journal of Accounting Research* 2023-era publication — Tier 1, cited via Alpha Architect summary, Oct 2024). This validates NLP-on-filings as genuine alpha infrastructure — for players with the data pipelines to industrialize it.
3. **Research acceleration.** Feature screening across thousands of candidate factors, anomaly detection in execution data, hypothesis generation, and code assistance are the places AI demonstrably compounds a quant team's productivity today. These are *upstream* uses: the live trading rules that result can remain simple, auditable, and rule-based.
4. **Regime detection & risk warning (useful, noisy).** Clustering/HMM-style regime models and vol-forecasting demonstrably help sizing and de-risking decisions; they are decision-support-grade, not oracle-grade. (General literature consensus — no single load-bearing citation offered; treat as Tier 2 consensus.)

### 5.2 Weaknesses and risks (evidence-backed)

1. **Information leakage manufactures fake AI track records.** "Profit Mirage" (arXiv:2510.07920, Oct 2025 — Tier 2): LLM trading agents (FinMem, FinCON, QuantAgent, TradingAgents et al.) evaluated on NASDAQ-100 in two market-condition-matched windows — inside vs beyond the model's knowledge cutoff — lost **51.5%–62.2% of Sharpe** and **50.2%–71.9% of total return** beyond the cutoff. Cause: pre-training contamination — the model *remembers* historical prices and narratives. Every impressive LLM-agent backtest that overlaps the training corpus should be presumed contaminated until proven otherwise.
2. **Published AI forecasting rarely survives contact with reality.** A review of 27 peer-reviewed AI market-forecasting experiments (2000–2018) found the published backtest results **did not translate into real-world outperformance** (Buczynski, Cuzzolin & Sahakian, *Int. J. of Data Science and Analytics*, 2021 — Tier 1, via Alpha Architect summary).
3. **Fund-level AI performance is unspectacular.** Eurekahedge AI Hedge Fund Index: **9.8% annualized Dec 2009–Jul 2024 vs S&P 500's 13.7%** (Tier 2, via IG citing index data, Nov 2024); cumulative Jan 2011–Jan 2020: **115% vs S&P 210% / MSCI World 133%** (Alpha Architect, Oct 2024 — Tier 2). Professional AI funds, in aggregate, did not beat passive equities over the sampled periods. (Index composition/self-reporting biases apply — in *both* directions.)
4. **Hidden overfitting scales with model capacity.** Everything in §4.2 applies to ML with more force: bigger hypothesis spaces mine noise more efficiently (Bailey et al.'s multiple-testing math — Tier 1). Data leakage via preprocessing (normalization fit on full history, label leakage, survivorship in training universes) adds failure modes rule-based systems don't have.
5. **Interpretability & maintainability.** When a deep model's live P&L diverges from backtest, there is often no decomposable "why." That turns live incidents from debugging into forensic research — an operational cost rule-based systems mostly avoid.
6. **Compute cost & latency.** Training/inference costs are real (GPU nodes on QuantConnect run to ~$1,000/mo — Tier 3 pricing signal); LLM inference latency makes them unsuitable in the execution path for anything fast; batch/asynchronous usage (research, pre-market analysis) is the workable pattern.
7. **Regulatory and fraud environment.** The CFTC (Jan 25, 2024 — Tier 1) states flatly: **"AI technology can't predict the future or sudden market changes"** and flags guaranteed/high-return bot claims as fraud markers, citing Mirror Trading International: a "proprietary bot" Ponzi that took **≥29,421 BTC (>$1.7B) from ~23,000 US participants** (2018–2021). The SEC/NASAA/FINRA joint alert (same day — Tier 1) documents unregistered platforms marketing "can't lose" AI systems and warns that giving investment advice/selling securities generally requires registration. **"AI" is simultaneously a technology and an active fraud vector; a legitimate product must visibly distance itself from the scam pattern.**
8. **Data rights & hallucination.** Training on proprietary market data, news, and filings raises licensing exposure (unresolved copyright landscape); LLMs fabricate plausible-sounding financial claims — any LLM output feeding decisions needs grounding and validation layers. (Tier 2 consensus; specific litigation not surveyed in this research.)
9. **No profit guarantee — structurally.** Markets adapt: any edge broadcast widely erodes (adaptive-markets argument as applied to AI funds by Swedroe/Alpha Architect, Oct 2024 — Tier 2; consistent with Falck et al.'s measured post-publication decay, Tier 2).

### 5.3 Net assessment

AI's *demonstrated* value in trading as of 2026 is concentrated **upstream** (research, feature extraction, text processing, screening, monitoring, anomaly/risk flags) and in **institutional-scale data industrialization** (EDGAR-style pipelines). Its value **in the live execution loop** — end-to-end LLM/RL traders — is unproven at best and leakage-inflated at worst. For a product builder: *sell AI as the research and risk copilot; keep the money path rule-based, bounded, and auditable.*

---

## 6. Three-Way Comparison: Traditional Quant vs AI Quant vs Manual Trading

### 6.1 Comparison matrix

Scale: ●●● strong / ●● moderate / ● weak. Judgments synthesize §4–§5 evidence; where evidence is thin, the cell says so.

| Dimension | Traditional rule-based quant | AI/ML-driven quant | Manual discretionary |
|---|---|---|---|
| **Return potential** | ●● Modest, cost-sensitive (CTA long-run ≈ 5–7% CAGR, Tier 2) | ●●(●) Higher *predictive* ceiling (GKX Sharpe ~2× linear, Tier 1) but shrinks after costs (Tier 1); fund-level evidence unexceptional (Tier 2) | ●–●●● Extreme dispersion; the retail median is negative (74–89% CFD accounts lose, Tier 1) |
| **Risk / drawdown control** | ●●● Codeable and enforceable (if honestly designed) | ●● Same tooling available, plus model-risk it must manage | ● Behaviorally weakest link |
| **Execution speed** | ●●● ms-level | ●●● (non-LLM inference) / ● (LLM in loop) | ● |
| **Strategy stability over time** | ●● Decays predictably (~5pp Sharpe decay/yr vintage, Tier 2); regime-fragile | ● Less stable: leakage + regime + drift (51–62% Sharpe decay past cutoff for LLM agents, Tier 2) | ●● A skilled human adapts; an unskilled one compounds errors |
| **Interpretability** | ●●● Full | ● Low (deep models) to ●● (trees/linear+SHAP) | ●● Narratable but post-hoc |
| **Development cost** | ● Low ($0–5k tooling; months) | ●●● High (data eng., compute, ML talent) | ● Low cash, years of screen time |
| **Maintenance cost** | ●● Re-validation treadmill | ●●● Data pipelines + retraining + drift monitoring | ●● Ongoing personal effort |
| **Data dependency** | ●● OHLCV/tick suffices | ●●● Alt-data hungry; institutional-scale footprints behind headline results (GKX: 900+ signals, Tier 1) | ● Low |
| **Technical barrier** | ●● MQL5/Python competence | ●●● ML + infra + finance | ● None to start (hence the loss statistics) |
| **Live deployment difficulty** | ●● Solved infrastructure (MT5, APIs) | ●●● Serving, latency, drift, kill-switches | ● Trivial (a login) |
| **Regulatory/compliance risk (as a product)** | ●● Software-tool framing possible; marketing rules still bite | ●●● "AI" claims are on regulators' 2024 fraud radar (Tier 1) | n/a (personal) / ●●● if selling advice |
| **Suitable asset classes** | FX/CFDs, futures, crypto, liquid equities | Data-rich: equities (cross-section), crypto (24/7), news-sensitive markets | Anything liquid enough to click |
| **Suitable users** | Disciplined semi-pro traders; product buyers | Quant teams; data-capable firms; researchers | Experienced full-time traders (a minority) |
| **Long-term sustainability** | ●● With continuous re-research | ●● Same treadmill, higher burn, bigger moat *if* data/infra proprietary | ● Rarely survives scaling or succession |

### 6.2 What the matrix actually implies

- **Return potential:** the only Tier-1-verified performance advantage in this entire report is *ML beating linear models out-of-sample in academic cross-sectional equity research* — and its Tier-1 rebuttal (costs/microcaps) arrives in the same breath. Neither traditional nor AI quant shows public evidence of retail-marketable "get rich" returns; Medallion (66% gross/39% net average 1988–2018, never a down year — Zuckerman estimates, Tier 2) is the famous exception, is capacity-capped (~$10–12B, internal money only), and is precisely the story scammers borrow.
- **Risk control is where automation genuinely dominates**, and it is the *least marketed* virtue in retail products because "we'll limit your losses" sells worse than "300% a year." That inversion — the real advantage being the unsold one — is the market gap §9 builds on.
- **Stability:** all three approaches decay; they differ in *how observably*. Rule-based decay is measurable (you can monitor live-vs-backtest divergence); AI decay hides behind model opacity; manual decay hides behind narrative. Products that make decay *visible* (tracking error dashboards, PBO/deflated-Sharpe reporting) convert this weakness into a feature.
- **Cost asymmetry:** traditional quant is cheap to build and cheap to fake; AI quant is expensive to build and *even easier to fake* (leakage). Trust infrastructure is therefore scarcer — and more valuable — than either technology.

---

## 7. Public Performance Data and Case Studies

Every row lists source, date, credibility tier, and limitations. **No number below is adjusted, extrapolated, or invented.** Where a metric the brief asked for (win rate, profit factor, capacity, user base) has no reliable public value, it is marked **missing**.

### 7.1 Institutional benchmarks (systematic/quant)

| Metric | Value | Period | Source (date) | Tier | Limitations |
|---|---|---|---|---|---|
| Medallion (RenTec) avg annual return | **66% gross / 39% net**, no losing year; $100 → ~$398.7M | 1988–2018 | Zuckerman's book data via Cornell Capital (Feb 2020), Visual Capitalist | 2 | Journalistic reconstruction; closed fund; unaudited publicly; unique capacity-capped case |
| Medallion 2024 return | ~**+30%** (~$12B internal capital) | 2024 | Hedgeweek (Jan 14, 2025), sourced to Zuckerman via LinkedIn | 2 (weak sourcing) | Second-hand, unverifiable |
| RenTec RIEF / RIDA | **+22.7% / +15.6%** | 2024 | Hedgeweek (Jan 14, 2025) | 2 | Unnamed sources; single year |
| Two Sigma Spectrum / ARE | **+10.9% / +14.3%** (~$60B AUM) | 2024 | Hedgeweek (Jan 14, 2025) | 2 | "Source close to the firm" |
| AQR Helix / Apex | **+17.9% / +15.1%** | 2024 | Hedgeweek (Jan 14, 2025) | 2 | Single year |
| Winton Fund ($13.1B) / CFM Stratus ($11.8B) | **+10.3% / +14.2%** | 2024 | Hedgeweek (Jan 14, 2025) | 2 | Single year |
| Context: S&P 500 | **+23%** — *most leading quant funds underperformed it in 2024* | 2024 | Hedgeweek (Jan 14, 2025) | 2 | Strong-beta year; not a like-for-like risk comparison |
| SG Trend Index | **+1.52% (Jun 2025); −15.05% trailing 12m; max DD 20.61%**; ~4.90% annualized since 2000 | to Jun 2025 | Top Traders Unplugged report (≈Jul 2025) tabulating SG data | 2 | Index of largest CTAs; survivorship at index level |
| BTOP50 (BarclayHedge) | **+1.51% (Jun 2025); −4.87% trailing 12m** | to Jun 2025 | Same | 2 | — |
| TTU Trend-Following composite | **7.04% CAGR, 20.81% max DD** since Jan 2000 (vs S&P500TR 7.70% CAGR, **50.95%** max DD) | 2000–2025 | Same | 2 | Composite construction by the publisher |
| Barclay CTA Index | **+3.61% YTD as of Jul 2024**; full-year 2023/2024 figures **missing** from retrievable sources this session | 2024 partial | TheFullFX citing BarclayHedge (2024) | 2 | Full annual table behind portal; do not extrapolate |
| Eurekahedge AI Hedge Fund Index | **9.8% annualized (Dec 2009–Jul 2024) vs S&P 500 13.7%**; cumulative 2011–2020: **115% vs 210% (S&P) / 133% (MSCI World)** | as stated | IG Prime insights (Nov 2024); Alpha Architect/Swedroe (Oct 2024) | 2 | Self-reported constituents; index migrated to With Intelligence; both survivorship and backfill biases possible |

### 7.2 Academic evidence (what's proven, at what scale)

| Finding | Value | Source (date) | Tier | Limitations |
|---|---|---|---|---|
| ML vs linear, US equities OOS | Long-short decile Sharpe **1.35 VW / 2.45 EW vs 0.61 / 0.83 (OLS)**; S&P timing Sharpe 0.77 vs 0.51 | Gu, Kelly & Xiu, *RFS* 33(5) (2020) | 1 — **verified 3-0** | Backtested research portfolios; **pre-cost**; gains concentrate in microcaps & shrink after costs (Avramov et al., *Mgmt Sci* 2023 — Tier 1) |
| Data scale behind that result | ~30,000 stocks, 60 years, 94 characteristics, 900+ signals | Same | 1 | Retail products do not train at this footprint |
| Overfitting bound | ≤5 yrs data + >~45 configs ⇒ IS Sharpe ~1 with **expected OOS Sharpe 0**; memory effects ⇒ **negative** OOS expectation | Bailey et al., *Notices of the AMS* (May 2014) | 1 | Idealized assumptions; direction robust |
| Hold-out unreliability; PBO framework | Standard hold-out "unreliable and inaccurate" for backtests; CSCV/PBO proposed | Bailey et al., *J. Computational Finance* (2017) | 1 (abstract source-verified) | — |
| Validator comparison | **CPCV ≫ K-Fold > Walk-Forward** at false-discovery prevention (lower PBO, better deflated Sharpe) | Arian et al., *Knowledge-Based Systems* 305 (2024) | 1 | Synthetic (controlled) environment |
| Strategy decay | 72 published equity factors: publication year explains ~30% of Sharpe decay variance; **+5pp decay per publication year**; overfitting variables +15% | Falck, Rej & Thesmar, arXiv:2105.01380 (May 2021) | 2 | Preprint (CFM authors); equities only |
| LLM-agent leakage | Sharpe **−51.5% to −62.2%**, returns **−50.2% to −71.9%** beyond knowledge cutoff (market-condition-matched windows) | "Profit Mirage," arXiv:2510.07920 (Oct 2025) | 2 | Preprint; NASDAQ-100 scope; specific agent frameworks |
| AI forecasting → reality gap | 27 peer-reviewed AI forecasting experiments (2000–2018): published results **didn't translate to real-world outperformance** | Buczynski et al., *Int. J. Data Sci. & Analytics* (Apr 2021), via Alpha Architect (Oct 2024) | 1 (via 2) | Cited through a summary; original not fetched this session |
| Institutional NLP edge | Funds bulk-downloading EDGAR 10-Ks earn excess returns (678 funds, 2000–2022) | Zeng & Zhou (JAR-era study, 2023), via Alpha Architect (Oct 2024) | 1 (via 2) | Same caveat |

### 7.3 Retail EA / bot / platform market data

| Metric | Value | Source (date) | Tier | Limitations |
|---|---|---|---|---|
| Retail CFD account loss rates (EU) | **74–89% lose money; avg per-client loss €1,600–29,000** | ESMA (Mar 27, 2018) | 1 | 2018 studies; leverage caps since imposed |
| Current broker disclosures (UK/EU) | e.g., **68%** (City Index), **70%** (IG); surveyed range **62–82%** | FCA-mandated firm disclosures; QuantifiedStrategies survey (2024-era) | 1 (per-firm) / 3 (survey) | Rolling 12-month windows; per-firm variance |
| ESMA product intervention | Leverage caps **30:1 → 2:1**, 50% margin close-out, negative balance protection, binary options ban | ESMA (2018), FCA PS19/18 permanent (Jul 2019) | 1 | Constrains high-leverage EA styles for EU/UK retail |
| MQL5 Market scale | **~14,000 products (~4,800 robots)**; "choice among 10,000 products" in current marketing; ~6,000 rentable; ~3,800 free; licenses **$30–$2,000+** | MetaQuotes article & market pages (article ca. 2018; marketing current) | 2/3 | Vendor-published counts; price range observational |
| MT4→MT5 shift | MT4/MT5 volume share: **65.3/34.7 (Q4 2023) → 55.8/44.2 (Q3 2024) → MT5 54.2% (Q1 2025)**; alternative platforms ~27% share (Q1 2025); MT4 closed to new brokers | Finance Magnates Intelligence (2024–2025) | 2 | Broker-volume based methodology |
| Crypto bot pricing | Pionex: 16 bots free + ~0.05% fee; 3Commas ~$29–99/mo; Cryptohopper $0–107.50/mo | Vendor pages & comparison sites (2025–26) | 3 | Changes frequently |
| Quant platform pricing | QuantConnect free tier; Team **$24**/Trading Firm **$48** per user/mo; nodes $14–1,000/mo | QC docs/reviews (2026) | 2/3 | Pricing page itself blocks fetch; cross-checked via docs |
| AI stock tools pricing | Trade Ideas from ~$118/mo; TrendSpider from ~$39/mo; Composer ~$32/mo; Danelfin $17–49/mo; Tickeron $60–250/mo | Vendor/roundups (2026) | 3 | Promotional tiers move |
| Advertised AI-tool performance | e.g., Trade Ideas "Holly" **"63.4% average annual return"** | Vendor claim via third-party roundup (2026) | 3 — **promo** | Simulated/vendor-reported; **not equivalent to reproducible real-world performance**; no independent audit found |
| Prop-firm economics | FTMO 2023 revenue **$203.9M**, op. costs $100.3M; payouts **$3.4M (2020) → $75.2M (2023)**, >$300k/day early 2024; industry challenge pass rate ~**14%**, ~**7%** ever paid, avg payout ~4% of account | TradeInformer filing analysis; FTMO statements; FPFX data (2024–2026) | 2 | Pass-rate figures industry-level, not FTMO-audited |
| Algo-trading market size | **$14.7B (2023) → $31.49B (2028E)**; algos ~60–73% of US equity volume | MarketsandMarkets & commonly cited estimates, via TradeAlgo blog (2026) | 3 | Second-hand citation of a research firm; definitional fuzziness |
| **Missing entirely** | Audited aggregate live P&L of any major EA vendor or crypto-bot user base; verified win rates; capacity figures; user-base P&L distributions | — | — | **No reliable public data exists** — vendors do not publish audited results; treat all such advertised numbers as promotional |

### 7.4 Fraud and failure case studies

1. **Mirror Trading International (bot-Ponzi archetype).** Marketed a proprietary forex "bot" guaranteeing ≥10%/month; took **≥29,421 BTC (>$1.73B at period-end value) from ~23,000 US participants** (2018–2021); operated as a Ponzi. (CFTC advisory & press release 8854-24, Jan 25, 2024 — Tier 1.) *Lesson: "guaranteed monthly returns + bot + referral tree" is the canonical scam stack; a legitimate product must be visibly not this.*
2. **The scam-EA business model (pattern evidence).** A practitioner exposé (MQL5 vendor blog, Mar 2026 — Tier 3, self-interested source, but mechanically consistent with regulator warnings) describes deliberate short-horizon extraction: curve-fit a flawless backtest → sell licenses at $50–200 for 2–6 months → reputation collapses → rebrand and relaunch. Variants: martingale EAs marketed on real-but-misleading "90% win rates" that blow up in 3–6 months; "free" EAs monetized via mandatory broker affiliate links, sometimes engineered to overtrade for commission volume. *Lesson: rankings and win rates are sales artifacts; incentive alignment is the differentiator worth building.*
3. **Grid/martingale terminal loss (single tracked account).** ForexTruck EA review (Forex Robot Lab — Tier 3): tracked balance **$2,000 → $25,000+ → $8** after one adverse move — months of "profits" erased in one tail event. *Lesson: high win rate + no hard portfolio stop = time bomb; this exact equity-curve shape is the industry's signature failure.*
4. **Regulatory posture (both US regulators, same day).** CFTC: "AI technology can't predict the future or sudden market changes" (Jan 25, 2024). SEC/NASAA/FINRA: unregistered platforms touting "Our proprietary AI trading system can't lose!"; registration generally required for advice/securities sales (Jan 25, 2024). *Lesson: marketing language is itself a compliance surface — the words on your landing page can be a violation before your code executes a single trade.*

### 7.5 What is missing — stated plainly

- **No audited, aggregate live-performance dataset exists for retail EAs or crypto bots.** Myfxbook/FX Blue verified accounts exist per-product but are self-selected (vendors display winners, delete losers); no platform publishes the full distribution. Any statement like "the average EA returns X%" is unsupportable from public data.
- **Win rates, profit factors, and capacity for commercial EAs:** vendor-reported only ⇒ **promo**.
- **Barclay CTA Index full 2023/2024 annual returns:** behind the BarclayHedge portal; only partial-year data was retrievable this session (do not quote full-year numbers without pulling the portal).
- **Eurekahedge AI index post-2024 monthly series:** migrated to With Intelligence subscription; the public 9.8% figure ends Jul 2024.

---

## 8. EA Deep Dive: The MT4/MT5 Ecosystem

### 8.1 Runtime environments

| Platform | Language | State (2025–26) | Notes for a builder |
|---|---|---|---|
| **MetaTrader 4** | MQL4 | Legacy; **closed to new broker licenses**; volume share fell from 65.3% (Q4 2023) to below MT5 by Q1 2025 (Finance Magnates — Tier 2) | Still a large installed base, but building MT4-first in 2026 is building on a decommissioned pier |
| **MetaTrader 5** | MQL5 | The default: **54.2% of combined MT volume, Q1 2025**, rising; multi-asset; tick-level tester; hosts the MQL5 Market | The distribution channel: Market + Signals + VPS built into the terminal |
| **cTrader** | C# (cBots) | Growing "alternative" share (~27% for all non-MT platforms, Q1 2025) | Cleaner API; smaller marketplace; broker-funded for traders |
| **NinjaTrader** | C# | Futures-centric (US retail futures) | Different regulatory posture (futures, not CFDs) |
| **TradingView** | Pine Script | Largest social charting base; automation via broker/webhook bridges | Alerts→execution needs middleware; huge top-of-funnel |
| **Crypto-native** | Python/APIs (ccxt, exchange SDKs), Hummingbot | 24/7 markets, no MT dependency | Different trust problem: exchange/API-key risk |

### 8.2 Distribution and "verification" infrastructure

- **MQL5 Market** (§3.3): ~10,000–14,000 products; $30–$2,000+ licenses; rental options; rankings driven by sales/popularity — **not verified profitability** (Tier 2/3).
- **Myfxbook / FX Blue:** third-party account-tracking; "verified track record" means *this account's* history is real — it does **not** mean the vendor didn't run 20 accounts and publish the survivor. Investor-password read-access to a long-running live account is the practical gold standard (practitioner consensus — Tier 3), and even that shows one sample path.
- **MQL5 Signals / copy platforms (ZuluTrade, Darwinex, etc.):** monetize strategies as subscriptions/AUM instead of licenses. Darwinex's regulated asset-management wrapper is the compliance-clean archetype (general knowledge — Tier 3; verify current terms).

### 8.3 EA strategy taxonomy — mechanics, appeal, and failure modes

| Strategy type | Mechanic | Why it sells | Real advantages | Characteristic risks / failure mode |
|---|---|---|---|---|
| **Martingale** | Double (or scale) size after each loss; exit at net recovery | Smooth equity curve, 90%+ win-rate optics | Exploits mean reversion *statistically often* | **Unbounded loss tails.** Trends outlast margin; one streak erases months (ForexTruck: $25k→$8 — Tier 3 case). Most sold variants have "no meaningful entry logic — fixed-interval recovery orders" (MQL5 practitioner post, Apr 2026 — Tier 3) |
| **Grid** | Ladder of buy/sell orders every N pips, no directional view | "Profits in ranging markets, no forecasting needed" | Genuine in sideways regimes; mechanically simple | Same tail as martingale when unhedged/no hard stop; inventory blows up on breakouts; swap costs accrue on held baskets |
| **Trend breakout** | Enter on range/volatility breakouts | Institutional pedigree (CTA logic) | Positive skew; survives on diversification | Whipsaw death by a thousand cuts in ranges (SG Trend −15% over 12m to Jun 2025 — Tier 2 — shows even pros bleed); retail versions rarely diversified enough |
| **MA crossover / indicator systems** | Classic rule crossovers | Easy to understand and backtest | Transparent; good teaching scaffold | Weak standalone edge after costs; the most curve-fit family on the Market (infinite parameter space) |
| **Arbitrage (latency/triangular/cross-broker)** | Exploit quote discrepancies | "Riskless profit" story | Real at institutional latency/infrastructure | Retail versions break broker ToS (banned, clawed back), or the "arb" is fake; capacity tiny; execution war you lose by default |
| **Hedging / "recovery" systems** | Offsetting long+short structures | Loss-masking optics ("no losing trades") | Legit uses: exposure netting, news straddles | Often martingale wearing a costume; swap+spread bleed; US FIFO/no-hedge rules complicate |
| **News trading** | Trade scheduled releases (NFP, CPI) | Big candles = big dreams | Volatility is real and scheduled | **Execution reality worst here:** spreads spike (gold ~8 pips at NY open, 30+ pip slippage — Tier 3, snippet-recovered), requotes, last-look rejections; backtests cannot simulate fill reality |
| **Scalping** | Many small, short-hold trades | High trade count = "consistent income" optics | Fast feedback loops for research | Cost-dominated: profit per trade ≈ spread; entirely broker/execution-dependent; tick-data quality artifacts inflate backtests (§8.4) |

### 8.4 Why EAs pass backtests and fail live — the seven mechanisms

1. **Multiple-testing overfitting (the big one).** Optimizer sweeps explore thousands of configurations; the math guarantees spectacular in-sample results with ~zero expected out-of-sample edge (MinBTL bound; PBO — Bailey et al., Tier 1). Vendors then market the survivor.
2. **Weak validation rituals.** Walk-forward — the MT-community standard — is the *weakest* of the compared validators at preventing false discoveries (Arian et al. 2024 — Tier 1). "Passed forward test" ≠ robust.
3. **Look-ahead and data-mining bias.** Subtle uses of future information (bar-close assumptions, repainting indicators, full-history normalizations); random systems look good by luck at scale (practitioner + Tier 1 literature). MT5's tick engine reduced but didn't eliminate this (MQL5 post, Jun 2026 — Tier 3).
4. **Tick-data quality theater.** "99% modeling quality" varies by data source and still can't reproduce live feed dynamics; backtest spreads are smoothed averages that miss news-window spikes (MQL5 posts, Jul 2025 & Apr 2026 — Tier 3, mechanically sound).
5. **Execution gap: asymmetric slippage & requotes.** Live slippage is regime-dependent and adverse-biased (fast markets fill you worse, not better); a modest edge dies by a thousand microstructure cuts (e.g., a breakout order slipping $43,000→$43,050 on BTCUSD — Tier 3 illustration). This kills scalping/news EAs first.
6. **Broker heterogeneity.** The same EA on two brokers produces materially different results — liquidity providers, execution models, rejection/partial-fill behavior, swap schedules (Tier 3, uncontroversial). A one-broker backtest is a one-lab experiment.
7. **Regime shift + strategy decay.** Even honest edges rot (~5pp Sharpe decay per publication-year vintage — Falck et al., Tier 2) and regimes rotate against any fixed rule set (SG Trend's 12-month −15% — Tier 2). A static EA is a depreciating asset sold as a durable good.

### 8.5 Builder's trap checklist

If you build an EA product, these are the traps the evidence says to engineer against:

- **Don't sell the backtest.** Publish PBO/deflated-Sharpe-style honesty metrics and a live, investor-password-verifiable account *from day one*; let the equity curve be modest and real. (Differentiator precisely because ~no one does it.)
- **No martingale/grid without a hard, portfolio-level stop** and pre-computed worst-case loss; better: don't ship unbounded-risk logic at all — it *will* find its tail event and your brand dies with the user's account.
- **Model costs pessimistically:** stress spreads at 2–5× averages around news; add adverse slippage; include swap; test across ≥3 brokers' data; if the edge survives, it might be real.
- **Cap the optimizer.** Track configurations tried; report it (the AMS paper's core demand — Tier 1); prefer CPCV-style validation over walk-forward alone (Tier 1).
- **Design for regime death:** monitoring that compares live tracking error to backtest expectation and *auto-de-risks* on divergence beats any static parameter set.
- **Mind the words:** no "guaranteed," no "win rate" headlines, no monthly-return promises — that's the regulator-documented scam lexicon (CFTC/SEC, Jan 2024 — Tier 1), and in the EU/UK your users are under ESMA/FCA leverage and disclosure rules anyway.

---

## 9. Product Opportunity Analysis

### 9.1 The pain points the evidence actually supports

| # | Pain point | Evidence anchor |
|---|---|---|
| P1 | **Backtest ≠ live** is the industry's central, documented failure | §4.2, §8.4 (Tier 1 math + practitioner consensus) |
| P2 | **No trust infrastructure**: rankings = sales; "verified" = survivor accounts | §7.4, §8.2 |
| P3 | **Tail-risk blowups** from high-win-rate designs | §8.3 case; martingale math |
| P4 | **Compliance is a minefield** for signals/advice/"AI" claims | §5.2(7), §7.4(4) (Tier 1) |
| P5 | **Risk discipline is the scarce good** — the prop-firm boom monetizes its absence ($203.9M FTMO revenue; ~14% pass rate) | §7.3 (Tier 2) |
| P6 | **Institutional validation methods exist but aren't productized** for retail/semi-pro (PBO, CPCV, DSR live in papers and Python libs) | §7.2 (Tier 1) |
| P7 | **AI hype gap**: buyers can't distinguish leakage-inflated AI claims from real capability | §5.2(1–3) (Tier 1/2) |

### 9.2 Candidate directions evaluated

**D1. Risk-control-first EA / equity-guardian layer** — *an EA (or EA-companion) whose product IS the risk engine: portfolio hard stops, per-trade and daily loss caps, news-window lockouts, prop-firm-rule compliance (daily/max drawdown guards), martingale detection for third-party EAs.*
- **Target users:** prop-challenge traders (FTMO et al. — a paying, risk-rule-constrained population by construction); EA users burned once; serious beginners.
- **Core value:** "keep me inside my risk rules" — aligned with P3/P5; measurable success (rule breaches prevented), no return promises needed.
- **Technical difficulty:** Low–moderate (MQL5 engineering, account-state math, broker quirks).
- **Compliance:** Comparatively low (software tool, no advice/signals) — but marketing language still governed (P4).
- **Business model:** One-time license + subscription for updates/monitoring dashboard; MQL5 Market + prop-community distribution.
- **Failure risk:** Medium. Risk control is unsexy; buyers want returns. Mitigation: sell to people *already forced* to care (prop traders lose their fee on a rule breach — the pain is monetized for you).

**D2. Multi-strategy portfolio system** — *uncorrelated strategy sleeves (trend + mean-reversion + carry) with portfolio-level allocation and risk budgeting.*
- **Target users:** semi-pro traders, small family offices.
- **Core value:** the institutional lesson (§4.1: diversification is where systematic actually wins) packaged accessibly.
- **Difficulty:** High — you must actually have several honest edges plus allocation logic; support burden heavy.
- **Compliance:** Moderate; starts resembling portfolio management if hosted → advice/management registration questions.
- **Business model:** Premium subscription; or Darwinex-style regulated wrapper.
- **Failure risk:** High for a first product — it's N strategy problems plus an allocation problem, and its proof cycle is measured in years.

**D3. Anti-overfitting strategy-validation platform (AI-assisted research lab)** — *upload/build a strategy → run CPCV, PBO, deflated Sharpe, multi-broker cost stress, regime slicing; LLM copilot for hypothesis generation and code; honest "robustness report" as the output artifact.*
- **Target users:** the ~tens of thousands of EA builders/StrategyQuant users/QuantConnect hobbyists and small prop/quant teams; EA *buyers* wanting due-diligence reports.
- **Core value:** turns Tier-1 science (P1/P6) into a product; converts the industry's core dysfunction into a service; the AI is *upstream* where it demonstrably helps (§5.3), so no leakage-inflated performance claims needed (P7).
- **Difficulty:** Moderate — validation math is published and implementable (open-source PBO/CPCV libraries exist); hard parts are data quality and UX.
- **Compliance:** Low — research tooling, no signals, no execution. Cleanest posture in the whole space.
- **Business model:** SaaS ($20–100/mo prosumer tiers mirroring QuantConnect/TrendSpider price points); B2B validation API for marketplaces/prop firms; a "validation badge" could become the trust layer P2 lacks.
- **Failure risk:** Medium. TAM smaller than the dream-selling market by definition (honesty filters out the biggest buyer segment); education-heavy sale. Mitigation: prop firms and EA marketplaces as B2B wedge — they *profit* from filtering bad strategies.

**D4. Trading-signal platform** — *sell entries/exits (human or AI generated).*
- **Target users:** convenience-seeking retail.
- **Core value:** hope, mostly (P2 works against you; you inherit the scam category's reputation).
- **Difficulty:** Low tech, brutal trust problem; performance decay is public and fast.
- **Compliance:** **Highest of all options** — signals ≈ investment advice in many jurisdictions (SEC/NASAA/FINRA registration warnings — Tier 1; ESMA marketing rules).
- **Business model:** subscriptions; churn-driven treadmill.
- **Failure risk:** High. **Not recommended** as a build target; the evidence base reads as a warning label for this exact product.

**D5. Semi-automated trading tool (execution/trade-manager copilot)** — *human decides, machine executes: sizing calculators, bracket automation, news lockouts, slippage tracking, journal analytics.*
- **Target users:** active discretionary retail/prop traders.
- **Core value:** attacks the execution gap (§8.4-5/6) and discipline (P5) without selling predictions.
- **Difficulty:** Low–moderate; crowded but fragmented (no dominant brand).
- **Compliance:** Low (tooling).
- **Business model:** $10–50/mo utility SaaS or one-time MT plugin; volume channel via MQL5 Market.
- **Failure risk:** Low–medium; modest ceiling but fast time-to-revenue; natural first product en route to D1/D3.

**D6. Low-risk automation for beginners** — *conservative, honest bot for first-time users.*
- **Core problem:** the honest version has low returns and thus no marketing hook against competitors who lie (P2); the environment itself (74–89% loss rates, leverage caps — Tier 1) means "beginner + leveraged trading" is structurally adverse. Ethical version drifts toward robo-advisory — a different, licensed industry.
- **Failure risk:** High as a business; **reputational/regulatory asymmetry** worst-in-class. Not recommended except as an education-first freemium funnel for D3/D5.

**D7. Strategy development platform for professionals** — *compete with QuantConnect/LEAN, StrategyQuant.*
- **Failure risk:** High: entrenched open-source incumbents, deep infrastructure cost, slow enterprise-ish sales. Only rational as a vertical specialization (e.g., "the MT5/prop-firm-native research stack") — which collapses back into D3.

### 9.3 Comparative view and recommendation

| Direction | Users | Value clarity | Tech difficulty | Compliance risk | Time-to-revenue | Failure risk | Verdict |
|---|---|---|---|---|---|---|---|
| D1 Risk-first EA | Prop/burned retail | High | Low–Med | Low–Med | Fast | Med | **Build (beachhead)** |
| D2 Multi-strategy system | Semi-pro | Med | High | Med | Slow | High | Later stage |
| D3 Validation platform | Builders, prop, marketplaces | High (unique) | Med | **Low** | Med | Med | **Build (core)** |
| D4 Signal platform | Retail | Low (trust-inverted) | Low | **High** | Fast | High | Avoid |
| D5 Trade-manager copilot | Active traders | High | Low | Low | **Fastest** | Low–Med | Good first wedge |
| D6 Beginner automation | Novices | Low (honesty penalty) | Med | High | Med | High | Avoid |
| D7 Pro dev platform | Quants | Med | **Very high** | Low | Slow | High | Avoid head-on |

**Recommended composite:** start with **D5 → D1 → D3** on the MT5/prop-firm axis: a trade-manager/risk-guardian utility earns fast distribution and trust (and produces the live execution-quality dataset that §10.3 says to validate first), the risk-control EA layer monetizes the prop-firm population whose pain is pre-monetized, and the validation platform is the defensible, compliance-clean core where the "AI quant" capability that actually works (research assistance, §5.3) belongs. This sequence sells *risk control and truth* into a market whose documented failures are *risk and truth* — rather than selling one more unverifiable promise into the world's most crowded promise market.

---

## 10. Conclusions and Recommendations

### 10.1 Real advantages vs marketing language

| Claim | Verdict | Basis |
|---|---|---|
| Automation enforces discipline, speed, multi-market scale, repeatability | **Real, mature** | §4.1; uncontroversial |
| Systematic = smoother ride (drawdown shaping vs equities) | **Real but modest** (≈equity-like CAGR at ~40% of the drawdown, long-run CTA data) | §4.1 (Tier 2) |
| Backtesting proves a strategy works | **False as commonly practiced** — provably generates false positives at retail workflow scale | §4.2 (Tier 1) |
| ML beats linear models at return prediction | **Real (research-grade)** — pre-cost, data-scale-dependent, microcap-concentrated | §5.1 vs Avramov (Tier 1) |
| "AI predicts markets" / AI bots with guaranteed or high fixed returns | **Marketing at best, fraud at worst** — regulators say so explicitly | §5.2(7) (Tier 1) |
| LLM-agent backtest track records | **Presume leakage-inflated** (−51–62% Sharpe past cutoff) | §5.2(1) (Tier 2) |
| AI funds outperform the market | **Not supported** by the public index record (9.8% vs 13.7% ann.) | §5.2(3) (Tier 2) |
| "Verified" vendor accounts prove product profitability | **Weak** — survivorship-selected single paths | §8.2 |
| Win rates as quality metric | **Actively misleading** (martingale sells 90% win rates into tail ruin) | §8.3 (Tier 3 + math) |

### 10.2 Mature vs unstable capabilities (2026)

**Mature, safe to build on:** execution automation (MT5/cTrader/exchange APIs); rule-based risk enforcement; backtesting *infrastructure* (with honest validation layered on top); grid/DCA as convenience (not alpha); copy/social plumbing; AI for research assistance, code generation, text summarization, factor screening, anomaly flagging.

**Unstable / not deployment-grade:** end-to-end LLM/RL live trading agents (leakage + latency + interpretability); AI as an execution-path decision maker; sentiment-alone strategies; retail "arbitrage"; any unbounded-risk recovery logic; performance-marketing-led products in the current enforcement climate.

### 10.3 What to validate first (before building anything)

1. **Execution-gap dataset:** collect live spread/slippage/rejection distributions across 3–5 target brokers (including news windows) for your target instruments; this is cheap, proprietary within weeks, and re-prices every backtest you'll ever run (§8.4).
2. **Strategy family robustness, not strategy performance:** PBO < ~20%, positive deflated Sharpe, CPCV-stable results across parameter neighborhoods and brokers *after* pessimistic costs — before any live capital (§7.2 methods).
3. **Live-vs-backtest tracking error** on small real capital (not demo — demo fills lie): 3–6 months minimum; predefine the divergence threshold that kills the strategy.
4. **Willingness-to-pay for risk control:** landing-page/waitlist tests against prop-trader communities (the segment with monetized pain) before writing the full product.
5. **Compliance perimeter for your jurisdiction(s):** tool vs signal vs advice classification; marketing-language review; EU/UK leverage-and-disclosure regime if targeting CFD users (Tier 1 sources in §7.3).

### 10.4 MVP blueprint (90–120 days, composite D5→D1)

- **Weeks 1–4:** MT5 trade-manager utility (bracket automation, position sizing, daily-loss lockout, news-window guard) + telemetry that records requested-vs-filled prices (starts your execution-gap dataset). Ship free/cheap on MQL5 Market for distribution and reviews.
- **Weeks 5–8:** Prop-rule guardian module (FTMO-style daily/max drawdown enforcement with pre-breach flatten); investor-password-verifiable demo→small-live accounts running 24/5; public dashboard of *risk metrics* (max DD, rule breaches prevented) — not returns.
- **Weeks 9–12:** Validation-report generator v0 (CPCV/PBO/DSR + cost-stress on user-supplied backtests) as a paid report; sell 10 manually to EA builders/buyers; that's the D3 seed and your pricing experiment.
- **Throughout:** no return promises anywhere; publish your methodology; every marketing claim regulator-proof (§8.5 language rules).

### 10.5 Mistakes to avoid (each traces to evidence)

1. Selling a backtest (Tier-1 math says it's ~meaningless as marketed) — §4.2.
2. Shipping unbounded martingale/grid logic — §8.3.
3. Trusting walk-forward + demo forward-testing as "proof" — §8.4(2,5).
4. Optimizing without counting configurations tried — §7.2 (MinBTL).
5. Launching signals/advice without registration analysis — §7.4(4).
6. Marketing with win rates, "guaranteed," monthly-return figures — the regulator-documented scam lexicon — §7.4.
7. Building MT4-first in 2026 — §8.1.
8. Putting an LLM in the live decision loop and calling its backtest a track record — §5.2(1).
9. Single-broker validation — §8.4(6).
10. Assuming a static edge: no live tracking-error monitoring and kill criteria — §4.2(3,4).

---

## 11. References

**Regulatory (Tier 1)**
1. CFTC — *Customer Advisory: AI Won't Turn Trading Bots into Money Machines* (Jan 25, 2024). https://www.cftc.gov/LearnAndProtect/AdvisoriesAndArticles/AITradingBots.html
2. CFTC — Press Release 8854-24 incl. Mirror Trading International case (Jan 25, 2024). https://www.cftc.gov/PressRoom/PressReleases/8854-24
3. SEC/NASAA/FINRA — *Investor Alert: Artificial Intelligence (AI) and Investment Fraud* (Jan 25, 2024). https://www.investor.gov/introduction-investing/general-resources/news-alerts/alerts-bulletins/investor-alerts/artificial-intelligence-fraud
4. ESMA — *ESMA agrees to prohibit binary options and restrict CFDs* (Mar 27, 2018; 74–89% loss data). https://www.esma.europa.eu/press-news/esma-news/esma-agrees-prohibit-binary-options-and-restrict-cfds-protect-retail-investors
5. FCA — PS19/18: *Restricting CFD products sold to retail clients* (Jul 2019). https://www.fca.org.uk/publication/policy/ps19-18.pdf ; FCA Handbook COBS 22.5 (loss-disclosure mechanics). https://handbook.fca.org.uk/handbook/cobs22/cobs22s5

**Peer-reviewed (Tier 1)**
6. Gu, Kelly & Xiu — *Empirical Asset Pricing via Machine Learning*, Review of Financial Studies 33(5):2223–2273 (2020). https://academic.oup.com/rfs/article/33/5/2223/5758276
7. Avramov, Cheng & Metzker — *Machine Learning vs. Economic Restrictions*, Management Science 69(5) (2023). https://pubsonline.informs.org/doi/10.1287/mnsc.2022.4449
8. Bailey, Borwein, López de Prado & Zhu — *The Probability of Backtest Overfitting*, J. Computational Finance 20(4) (2017). https://www.davidhbailey.com/dhbpapers/backtest-prob.pdf
9. Bailey, Borwein, López de Prado & Zhu — *Pseudo-Mathematics and Financial Charlatanism*, Notices of the AMS 61(5) (May 2014). https://www.ams.org/notices/201405/rnoti-p458.pdf
10. Arian, Norouzi Mobarekeh & Seco — *Backtest overfitting in the machine learning era*, Knowledge-Based Systems 305 (2024). https://www.sciencedirect.com/science/article/abs/pii/S0950705124011110
11. Buczynski, Cuzzolin & Sahakian — review of AI market-forecasting experiments, Int. J. Data Science & Analytics (2021) — cited via [Alpha Architect summary](https://alphaarchitect.com/ai-funds/).
12. Zeng & Zhou — hedge funds' EDGAR textual analysis (2023-era) — cited via same Alpha Architect summary.

**Preprints & industry research (Tier 2)**
13. *Profit Mirage: Revisiting Information Leakage in LLM-based Financial Agents* — arXiv:2510.07920 (Oct 2025). https://arxiv.org/abs/2510.07920
14. Falck, Rej & Thesmar (CFM) — *Why and how systematic strategies decay* — arXiv:2105.01380 (May 2021). https://arxiv.org/abs/2105.01380 / https://www.cfm.com/wp-content/uploads/2022/12/312-2021-05-Why-and-how-systematic-strategies-decay.pdf

**Index & fund performance (Tier 2)**
15. Hedgeweek — *Renaissance Tech and Two Sigma lead 2024 quant gains* (Jan 14, 2025). https://www.hedgeweek.com/renaissance-tech-and-two-sigma-lead-2024-quant-gains/
16. Top Traders Unplugged — *Trend Following Performance Report, June 2025* (SG Trend/BTOP50/TTU data). https://www.toptradersunplugged.com/trend-following-performance-report-june-2025/
17. Eurekahedge AI Hedge Fund Index (With Intelligence). https://www.eurekahedge.com/Indices/IndexView/Eurekahedge/683/Eurekahedge-AI-Hedge-fund-Index ; performance context via [IG Prime](https://www.ig.com/za/prime/insights/articles/has-artificial-intelligences-impact-on-hedge-funds-been-overhype-241121) (Nov 2024) and [Alpha Architect](https://alphaarchitect.com/ai-funds/) (Oct 2024).
18. BarclayHedge — Barclay CTA Index portal. https://portal.barclayhedge.com/cgi-bin/indices/displayCtaIndex.cgi?indexCat=Barclay-CTA-Indices&indexName=Barclay-CTA-Index ; partial-2024 reading via [The Full FX](https://thefullfx.com/ctas-continue-to-erode-2024-gains/).
19. SG Prime Services Indices. https://wholesale.banking.societegenerale.com/en/prime-services-indices/
20. Medallion 1988–2018 figures — Cornell Capital Group (Feb 2020) https://www.cornell-capital.com/blog/2020/02/medallion-fund-the-ultimate-counterexample.html ; Visual Capitalist https://www.visualcapitalist.com/growth-of-100-invested-in-jim-simons-medallion-fund/

**Ecosystem & market structure (Tier 2/3)**
21. Finance Magnates — MT4/MT5 volume-share reporting (2024–2025), incl. *MT5 Overtakes MT4 in Trading Volume* (Q1 2025). https://www.financemagnates.com/forex/products/exclusive-after-15-years-mt5-overtakes-mt4-in-trading-volume-marking-end-of-an-era/
22. MetaQuotes — *14,000 trading robots in the MetaTrader Market* (MQL5 Articles #5194) https://www.mql5.com/en/articles/5194 ; MQL5 Market pages https://www.mql5.com/en/market ; MetaTrader Market overview https://www.metatrader5.com/en/automated-trading/mql5market
23. TradeInformer — *What FTMO tells us about prop firm finances* (2024). https://tradeinformer.com/prop-weekly/what-ftmo-tells-us-about-prop-firm-finances ; FTMO payout statements https://ftmo.com/en/blog/we-pay-millions-in-payouts-to-our-ftmo-traders/ ; CoinLaw FTMO statistics https://coinlaw.io/ftmo-statistics/
24. QuantConnect — pricing/tier documentation. https://www.quantconnect.com/pricing/ ; https://www.quantconnect.com/docs/v2/cloud-platform/organizations/tier-features
25. Crypto bot pricing — 3Commas https://3commas.io/pricing ; comparison: CoinCodeCap https://coincodecap.com/3commas-vs-pionex-vs-cryptohopper
26. AI stock tool pricing — Danelfin https://danelfin.com/pricing/annual ; Composer https://www.composer.trade/pricing ; roundup https://www.tradealgo.com/trading-guides/ai-trading/best-algorithmic-trading-platforms-in-2026-a-complete-comparison

**Practitioner EA material (Tier 3 — vendor/community blogs; quotes partly snippet-recovered due to fetch blocks)**
27. MQL5 Traders' Blogs — *Why Your Expert Advisor Worked in Backtest and Failed Live* (Jun 28, 2026). https://www.mql5.com/en/blogs/post/772056
28. MQL5 Traders' Blogs — *Why Gold EAs That Work in Backtests Die in Live Trading* (Apr 21, 2026). https://www.mql5.com/en/blogs/post/769035
29. MQL5 Traders' Blogs — *Why Most Martingale EAs Blow Up* (Apr 1, 2026). https://www.mql5.com/en/blogs/post/768549
30. MQL5 Traders' Blogs — *How Forex Robot Scams Actually Work* (Mar 10, 2026). https://www.mql5.com/en/blogs/post/767934
31. MQL5 Traders' Blogs — *Not All 99% Backtests Are Equal: Tick Data Quality in MT5* (Jul 15, 2025). https://www.mql5.com/en/blogs/post/762517
32. Forex Robot Lab — *ForexTruck EA Review* (grid/martingale loss case). https://forexrobotlab.com/forextruck-ea-review/
33. QuantifiedStrategies — CFD loss-rate survey. https://www.quantifiedstrategies.com/cfd-trading-statistics/ ; Medallion returns compilation https://www.quantifiedstrategies.com/medallion-fund-returns/

---

## 12. Full Disclaimer

This document was prepared **solely for market research and product-strategy analysis**. It is **not** investment advice, trading advice, legal advice, or a solicitation to buy or sell any financial instrument, and it must not be relied upon for investment decisions. Trading foreign exchange, CFDs, futures, cryptocurrencies, and equities involves substantial risk of loss; leveraged retail products in particular are documented by regulators to produce losses in **62–89% of retail accounts** (ESMA 2018; FCA-mandated firm disclosures). **No trading system referenced or proposed here — rule-based, AI-driven, or otherwise — can guarantee profits or prevent losses.** Performance figures cited are historical, often unaudited, sometimes explicitly promotional (labeled as such), and are not predictive of future results. Product prices, regulations, and platform facts change; verify all figures against primary sources before relying on them. Any product built on the recommendations herein requires independent legal/compliance review in every target jurisdiction. Nothing here creates any advisory relationship.

*Report compiled July 4, 2026, from public sources retrieved June–July 2026 via a multi-agent research pipeline with partial adversarial verification (see §2). Errors and omissions possible; primary sources govern.*
