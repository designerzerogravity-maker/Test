# Groww India Day Trading Research

**Goal studied:** Earn roughly **₹200–500 net per day** via day trading on **Groww (India)**  
**Date:** 10 Aug 2026  
**Status:** Research only — not financial advice. Markets involve substantial risk of loss.

---

## Verdict (short)

Technically possible for a skilled, disciplined trader with enough capital — **not a reliable “daily salary”** for most people.

| Question | Answer |
|----------|--------|
| Can Groww support day trading? | **Yes** — equity intraday, F&O, commodities, Terminal, Option Chain, API |
| Is ₹200–500/day a realistic *guaranteed* income? | **No** — non-guaranteed; SEBI data shows ~**91%** of individual F&O traders lose money |
| Practical capital for that *aspirational* target | Roughly **₹1–5 lakh+** (below ~₹50k, fees dominate) |
| Best first build | Fee/break-even + risk/position-size + trade journal (not a profit bot) |

---

## 1. What Groww offers day traders

### Products
- **Equity intraday (MIS)** — same-day square-off
- **Futures & Options** — index/stock derivatives via Terminal + Option Chain
- **Commodities** — crude, gold, silver, etc. (MCX)
- **Currency derivatives** (platform marketing; confirm availability in your account)
- **Pledge** — use holdings as F&O collateral
- **Groww Trade API / Groww Cloud** — algo & automation (~₹499/month + taxes early-bird pricing on trade-api page)

### Useful built-ins
- Groww Terminal (charts, orders, positions, watchlists)
- Option chain / basket views
- Stock screeners (more fundamental/tech filters than pure momentum day-trade scanners)
- GTT / smart orders (API mentions OCO/GTT)
- Brokerage & margin calculators on site

### Gaps (where custom software helps)
| Gap | Why it matters |
|-----|----------------|
| **No paper trading** on Groww | Must practice elsewhere or simulate |
| Weak **intraday scanners** (volume spike, VWAP, breakout lists) | Manual chart hunting |
| No **backtester** | Hard to validate rules |
| No **fee-aware journal / risk dashboard** | Easy to ignore costs & overtrade |
| API is paid | Automation has a fixed cost (~₹499 + GST/month) |

Official refs:
- https://groww.in/pricing/
- https://groww.in/futures-and-options
- https://groww.in/trade-api
- https://groww.in/trade-api/docs/python-sdk

---

## 2. Fee structure that eats small daily targets

### Equity intraday (from Groww pricing / help, Aug 2026)

| Charge | Typical rate |
|--------|----------------|
| Brokerage | Lower of **₹20** or **0.1%** per executed order (min **₹5** rules as published) |
| STT | **0.025%** on **sell** |
| Stamp duty | **0.003%** on **buy** |
| Exchange txn | NSE ~**0.00297%** / BSE ~**0.00375%** (buy & sell) |
| SEBI turnover | **0.0001%** (buy & sell) |
| IPFT (NSE) | **0.0001%** (buy & sell) |
| GST | **18%** on brokerage + applicable charges |
| Auto square-off | **₹50 + GST** per position if left open for system square-off |

### F&O
- Brokerage typically **₹20 flat per order** (confirm on F&O pricing page)
- STT/CTT and exchange charges differ by futures vs options — always recalculate per trade

### Fee drag example (illustrative)

Trade ₹10,000 buy → ₹10,100 sell (₹100 gross):

- Round-trip brokerage + statutory + GST often lands near **~₹25–35** (order size dependent)
- Net ≈ **₹65–75**, not ₹100
- To clear **₹300 net**, you may need **~₹350–450+ gross** after fees/slippage — or larger ticket sizes where % fees matter less but ₹20 caps apply

**Implication:** Many tiny scalps → death by fees. Prefer **few, fee-aware trades** with clear R:R.

---

## 3. Capital math for ₹200–500 / day

Daily target as % of capital (gross, before fees):

| Capital | ₹200/day | ₹350/day | ₹500/day |
|---------|----------|----------|----------|
| ₹25,000 | 0.8% | 1.4% | 2.0% |
| ₹50,000 | 0.4% | 0.7% | 1.0% |
| ₹1,00,000 | 0.2% | 0.35% | 0.5% |
| ₹2,00,000 | 0.1% | 0.175% | 0.25% |
| ₹5,00,000 | 0.04% | 0.07% | 0.1% |

Notes:
- **1%+ per day compounded is extremely aggressive** and rarely sustainable.
- With ~5x max equity intraday leverage (broker + SEBI margin constraints; often ~20%+ margin), buying power rises but **risk of ruin** also rises.
- Risk rule of thumb: risk **1–2% of capital per trade**, max daily loss e.g. **2–3%** then stop for the day.
- At ₹50k capital, 1% risk = ₹500 — so a ₹500 *profit* target with ₹500 *risk* is essentially a 1:1 day; losing days wipe winning days quickly.

**Practical framing:** Treat ₹200–500 as an **aspirational net** after costs on good days — not a paycheck. Aim first for **process consistency** (journal, risk limits), then scale capital.

---

## 4. Regulation & market reality (India)

### Margins / leverage
- Peak/upfront margin regime ended the old ultra-high “intraday leverage” era.
- Equity intraday typically needs meaningful margin (~20%+ class of requirement depending on stock/broker).
- Options: **full premium upfront** for buyers under recent SEBI measures; lot sizes / weekly expiry rationalisation increased capital needed for index options.
- Expiry-day speculation is more constrained; retail should not treat weekly options as ATM cash machine.

### SEBI F&O retail outcomes (FY25 study, widely reported)
- ~**91%** of individual equity derivatives traders made **net losses**
- Aggregate individual net losses ~**₹1.05–1.06 lakh crore** in FY25 (after transaction costs)
- Average loss per person on the order of ~**₹1.1 lakh** (order of magnitude from press coverage of the study)

**Takeaway:** Odds are against casual F&O income strategies. Equity cash intraday is also hard; F&O is statistically worse for retail.

### Tax (high-level — confirm with a CA)
- Intraday equity P&L generally treated as **speculative business income**
- Usually filed via **ITR-3**; losses have set-off / carry-forward constraints
- Brokerage and related costs may be deductible as business expenses — **get professional tax advice**

---

## 5. Strategy lanes (what “can be done”)

Ranked for a **small daily rupee goal** on Groww:

### A. Equity cash intraday (best first lane for beginners)
- Liquid large-caps / index heavyweights only
- 1–2 setups/day max (open range breakout, VWAP reclaim, opening drive fade — pick **one** playbook)
- Hard stop + time stop (no “hope”)
- Square off well before auto square-off window

### B. Defined-risk options (advanced only)
- Prefer debit spreads / defined risk over naked selling or lottery OTM buys
- Capital & lot size may make ₹200–500 days *possible* but variance is violent
- SEBI loss stats apply heavily here

### C. Futures
- Large margins; overkill for ₹200–500 unless already experienced
- One wrong tick can erase many “good days”

### D. What to avoid for this goal
- Signal Telegram groups / “guaranteed ₹500/day”
- Offshore binary-style apps
- Overtrading to “make back” fees
- Holding intraday losers into delivery by accident without plan (and without margin)

---

## 6. What we should build (recommended roadmap)

### Phase 0 — Research (this doc) ✅
### Phase 1 — MVP toolkit (recommended next)
1. **Groww fee & break-even calculator** (equity MIS + simple F&O)
2. **Position size planner** (capital, stop ₹/%, risk % → quantity)
3. **Daily risk dashboard** (target ₹200–500, max loss kill-switch, fee estimate)
4. **Trade journal** (CSV/local DB): entry, exit, fees, R-multiple, notes

### Phase 2 — Practice layer
- Paper-trade logger that mimics Groww order fields (MIS/CNC, product type)
- Pre-market checklist (liquidity, gap %, news, earnings)

### Phase 3 — Optional Groww API (paid)
- Read-only: LTP, positions, order history sync into journal
- Later: alerts → manual confirm → order (never fully unsupervised without kill-switch)

### Explicit non-goals (for now)
- “AI that prints ₹500/day”
- Fully autonomous live trading without user risk controls
- Scraping Groww in violation of ToS

---

## 7. Honest success criteria

Before treating trading as income:

1. **50+ journaled paper/sim trades** with written rules  
2. Positive expectancy **after fees**  
3. Max drawdown understood and acceptable  
4. Separate living expenses from trading capital  
5. Daily loss limit never broken “just this once”

If those fail, the tool still succeeds as a **loss-prevention & learning system**.

---

## 8. Sources checked

- Groww Pricing: https://groww.in/pricing/
- Groww intraday charges help article
- Groww Trade API: https://groww.in/trade-api and Python SDK docs
- SEBI retail F&O P&L studies (FY24/FY25) via Economic Times / Indian Express / Fortune India summaries
- Browser walkthrough of Groww product pages (Aug 2026)

Screenshots (local artifacts from research session):
- `groww-pricing.webp`
- `groww-intraday-charges.webp`
- `groww-no-paper-trading.webp`
- `capital-guidance.webp`
- `sebi-retail-losses.webp`
