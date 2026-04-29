# Notch — Patent Strategy

**Date:** 2026-04-28
**Author:** Igor / Claude session
**Status:** Pre-filing strategy memo, ready for attorney conversation

---

## TL;DR

File a **portfolio of 3–4 provisional patents** in the next 30 days covering the core technical mechanisms of the KOPS oracle and Tail.trade settlement architecture. File US + UK via PCT route. All-in cost over 5 years: ~$100–150k. Near-term commitment: $15–25k for provisional bundle.

The case is not "patent-pending in the deck." The case is that Notch has accumulated 18+ months of genuinely novel technical work across pricing, settlement, and data integrity — and a portfolio of structural claims gives real leverage against US-domiciled incumbents (DraftKings, FanDuel, Flutter, Entain, Kalshi, Polymarket post-pivot) if any of them ship a copycat in the next 5 years.

It does **not** help against offshore Solana forks. They will ignore US/UK patents.

---

## What we'd file

Four separate inventions, filed as a coordinated provisional bundle so claims don't overlap or undermine each other.

### Filing 1 — Continuous non-expiring sports position with frozen-reference settlement

**The structural / category-defining claim.** Drafted to read on any product in this category, regardless of formula.

> A computer-implemented method for operating a non-expiring derivative position on a sports entity, comprising: maintaining a continuous numerical index value for the entity; deriving and freezing, prior to a sporting event, an expected outcome reference from one or more probabilistic data sources; receiving the actual outcome of the event; updating the continuous index by a function of the difference between actual and frozen-expected outcome; and settling open positions against the updated index, where positions have no fixed expiration.

To design around this claim, a competitor must abandon at least one of: continuous index, non-expiring positions, or pre-event probability reference. All three options produce a worse product.

This is the most important filing. If we only do one, this is the one.

### Filing 2 — Two-layer state-plus-carry decomposition for perpetual sports pricing

The B + M1 architecture. Realized state (B, updated only on settlement) combined with a forward carry term (M1, computed via Bayesian solve over upcoming fixtures with time-decayed weighting). Claim the decomposition itself: the separation of realized index from forward expectation, where forward expectation is derived from a probabilistic solve over scheduled future events.

This is the mechanism that makes the derivative continuously priceable between matches without faking liquidity. Any competitor in this category needs *some* equivalent mechanism — the claim is hard to design around.

### Filing 3 — Multi-source fixture binding for deterministic derivative settlement

The phantom resolution system (Steps A/B/C from PR #14). Method for binding identifiers across heterogeneous external sports data providers with incompatible ID schemes, with date-bounded rescue, ambiguity detection, and canonical-fixture promotion to ensure deterministic settlement.

Solves a concrete technical problem — patent attorneys like this kind of claim because it's unambiguously technical, clearly novel, and clearly not an abstract idea. Will sail through both USPTO Alice analysis and UKIPO § 1(2) technical-contribution analysis.

### Filing 4 — Cross-source data integrity reconciler for continuous index oracles

Inline reconciler architecture (Odds API ↔ API-Football). Detects divergence between independent data sources before contaminated data flows into settlement. Daily-digest expected-vs-ingested heartbeat (Check K family) catches systemically missing data.

Lower priority than 1–3 but cheap to bundle into the same provisional and adds another layer that competitors trip on.

### Optional bundle item — Translation-invariant engine architecture

The faithful-transmission property. Engine state can be reseeded mid-operation without breaking forward settlement consistency. Subtle and unusual enough to be worth claiming. Can be folded into Filing 2 as a dependent claim rather than a separate filing.

---

## What we won't file and why

| Element | Reason |
|---|---|
| Three-entity structure (oracle / DEX / consumer app) | Business method, not patentable. Already public in the deck. |
| Builder Codes model | Hyperliquid prior art. Business method anyway. |
| Waitlist / referral / founding holder mechanics | Pure business method. Robinhood-style mechanics are well-trodden. |
| Specific calibration parameters (γ=0.08, α=0.40, BT window 30d, etc.) | Trade secret. More durable than a patent — competitors can't reverse-engineer parameters from observed prices, and disclosure forces us to teach competitors the recipe. |
| League-specific calibrations and closed-universe corrections | Trade secret. Same logic. |
| The exact V5.5-FINAL formula | Trade secret. The patent claims the *category* and *architecture*, not the specific formula. |

The pattern: claim the category-defining structural elements, keep the calibration recipe as trade secret. Best of both.

---

## Jurisdiction strategy: US + UK via PCT

### Mechanics

1. **US provisionals (next 30 days)** — $15–25k for the bundle. Locks priority date globally.
2. **PCT international (month 12)** — $15–25k. One filing, gives 30 months from priority date to commit to specific countries.
3. **National phase (month 30)** — US utility + UK national. ~$60–100k through grant for the bundle.

Total over 5 years: **~$100–150k**, but only $15–25k is committed in the near term. Real money commits later, and only if traction justifies it.

### Why US + UK

**US:** Where the actual revenue threat lives. CFTC-licensed entrants, DraftKings, FanDuel, Kalshi, Polymarket post-pivot — all sue-able in US federal court. A clean structural patent against a public infringer is a $10–50M settlement conversation, and the threat alone is leverage at exit.

**UK:** The actual betting incumbents are UK-domiciled. Flutter (FanDuel parent), Entain, Bet365, William Hill, Paddy Power. UK High Court Patents Court is fast and technically sophisticated. A UK injunction against Flutter UK ops is a serious settlement lever even when the infringement is happening at the US subsidiary. Premier League is also the most-traded league globally — if anyone copies, UK is where they launch first.

**EPO (Germany / France / Spain / Italy):** Worth considering at month 30 (~$15–25k more) given Bundesliga / La Liga / Serie A are top-5 leagues in our oracle. Don't commit now. Decide based on traction.

### UK drafting requirement

UKIPO is stricter on software patents than USPTO. Claims must demonstrate technical contribution under § 1(2) — solving a technical problem with a technical means. This affects the spec from day one, not just examination arguments.

The Notch inventions naturally satisfy this, but only if framed correctly:
- *Deterministic settlement in a distributed system* — frozen reference snapshot is a technical mechanism for cross-node settlement determinism without consensus replay
- *Real-time index updates from heterogeneous probabilistic sources* — devigging + median consensus across bookmakers is signal processing, not a business rule
- *Cross-provider identifier binding* (Filing 3) — concrete technical problem, clearly technical solution

A US-only patent attorney will draft this in a way that breezes through USPTO and dies at UKIPO. **Need an attorney with fintech + UK/EPO experience from day one.** Cost difference is minimal, outcome difference is huge.

---

## What the patents give us

### Real value

1. **Defensive moat against US incumbents.** Any of DraftKings, FanDuel, Flutter, Entain, Kalshi, Polymarket shipping a copycat → settlement conversation. Probability of use: low (5–15%), value if used: $10–50M.
2. **M&A premium.** A strategic acquirer (incumbent betting operator wanting to enter perp sports) pays a premium for clean issued IP because it removes uncertainty from their roadmap. Estimated: $5–15M on a $100M+ exit.
3. **Series A / B credibility with sophisticated funds.** Real fintech VCs notice not the "patent pending" sticker, but the fact that we understood our technical moat well enough to claim it specifically. Filing 3 (phantom resolution) in particular demonstrates engineering depth in a way a deck doesn't.
4. **Priority date insurance.** If we don't file and someone else files first on overlapping art, we lose the ability to operate freely in our own product. Provisionals at $15–25k are cheap insurance against this.

### What patents don't give us

- Protection against offshore Solana forks (they ignore US/UK patents)
- Anything operational — liquidity, distribution, oracle history, brand
- Regulatory benefit (CFTC perp framework path is independent)
- Quick credibility with crypto-native VCs (they weight patents at near zero)

The actual moats remain: liquidity history, multi-year oracle track record, Builder Code lock-in, brand with retail, first-mover under CFTC perp framework. Patents are insurance, not the foundation.

---

## Prior art / risk

### Football Index (UK, 2015–2021) — the one that matters

Player-level tradeable shares, perpetual, paid event-driven dividends on media mentions and match performance. UK-regulated as betting, collapsed 2021 after a license revocation.

**Differentiation that survives:**
- Team-level (not player-level) — different underlying
- Perpetual derivative structure (not equity-style shares with dividends) — different instrument
- **Settlement against frozen pre-event bookmaker probability consensus** — Football Index paid event-driven dividends, never ran a continuous index updated by an expected-vs-actual delta. This is where Filing 1's claim should anchor.

### Other prior art to address in the spec

- Hyperliquid (perp DEX architecture) — different underlying, no team-strength index
- Polymarket / Kalshi (event contracts) — binary expiring, structurally different
- ClubElo / FiveThirtyEight (Elo-style team ratings) — published ratings, not tradeable derivatives, no settlement mechanism
- Sorare / DraftKings Reignmakers (NFTs / fantasy) — discrete items, not continuous index
- Fanatics / sports collectibles markets — not derivatives

The patent attorney will run a formal prior art search. The above is the obvious-to-us list to brief them on.

---

## Drafting principles

1. **Structural, not formulaic.** Claim the category-defining mechanism, not the specific formula. Anyone in this product category trips on a structural claim; a formula claim is trivially designed around.
2. **Independent claims broad, dependent claims specific.** Independent claims define the moat. Dependent claims add specifics (Bradley-Terry MAP, time-decay weights, gravity term) that strengthen position during prosecution but aren't the primary defense.
3. **Spec rich enough to support multiple claim families.** Provisional spec should describe the full system in enough detail that we can carve out additional dependent claims during conversion if the prior art search surfaces issues.
4. **Don't include the calibration recipe.** Specific parameter values (γ, α, BT window, decay half-life) stay out. They're trade secret. The spec describes the mechanism; the values are implementation detail and don't need to be disclosed.
5. **Frame technical problems explicitly.** UKIPO needs this. Even for USPTO, post-Alice, framing the technical problem makes the claim more durable against § 101 challenges.

---

## Next 30 days

| Day | Action | Owner |
|---|---|---|
| 1–7 | Identify and engage patent attorney with fintech + UK/EPO experience. Brief on the bundle. Sign engagement letter. | Igor |
| 1–3 | Claude drafts technical spec sections for Filings 1–4. Output: 4 docs, 8–15 pages each, structured as patent attorney can convert directly. | Claude |
| 7–14 | Attorney runs prior art search, refines claims. We review and respond. | Attorney + Igor |
| 14–28 | Attorney drafts provisional applications. We review final claims. | Attorney + Igor |
| 28–30 | File provisionals. Priority date locked. | Attorney |

**Decision points in next 12 months:**
- Month 6: Review traction and competitive landscape. Decide whether to convert all four provisionals or drop some.
- Month 12: File PCT for surviving inventions. Real second commitment of ~$15–25k.

**Decision points at month 30:**
- National phase entry. US + UK confirmed if traction is real. EPO decided based on European volume.

---

## Cost summary

| Phase | Timing | Cost | Cumulative |
|---|---|---|---|
| Provisional bundle (US, 4 inventions) | Month 0 | $15–25k | $15–25k |
| PCT international filing | Month 12 | $15–25k | $30–50k |
| US national phase + prosecution | Months 30–48 | $25–40k | $55–90k |
| UK national phase + prosecution | Months 30–48 | $20–35k | $75–125k |
| EPO (optional, decide at month 30) | Months 30–48 | $20–30k | $95–155k |

All numbers assume a single attorney shop and a clean prosecution (no major office actions requiring substantial argumentation). Add 20–30% contingency for office actions on tougher claims.

---

## What's not in scope of this memo

- Trademark strategy (separate exercise — Notch, KOPS, Tail.trade marks)
- Trade secret protection program (NDA hygiene, employee IP assignment, repository access controls — operational not legal)
- Regulatory IP (CFTC submissions, exchange license filings — different track entirely)
- Defensive publication strategy for items we choose not to patent (worth considering for the calibration approaches we want to ensure no one else can patent against us)

---

## Open questions for attorney conversation

1. Should Filings 1 and 2 be combined into one application with multiple independent claims, or kept separate? (Tradeoff: cost vs. flexibility during prosecution.)
2. Provisional → utility timeline: 12 months standard, but is there a strategic reason to convert earlier (e.g., publication for defensive value)?
3. Does any jurisdiction we're considering have a grace period issue with the deck already being public? (Standard answer: US has 1-year grace for own disclosures, UK/EPO does not — so PCT must file within 12 months of any deck-as-public-disclosure event.)
4. Is the V5.5-FINAL methodology document itself a publication risk? (If it's been shared with VCs under NDA, probably not. If it's been published on a blog or shared without NDA, that resets the clock.)

---

*This memo is a strategy framework, not legal advice. Final claims, scope, and filing strategy must be set with a licensed patent attorney. Use this document to brief the attorney and structure the conversation, not as a substitute for it.*
