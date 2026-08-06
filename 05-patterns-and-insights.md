# 05 — Patterns & Insights

The meta-analysis. What unifies the top performers and what nobody is saying publicly.

---

## The Unifying Principle

Every high-performing AI bug bounty system does ONE thing:

> **Refuses to accept the model's first "nothing here / I'm done" signal.**

| System | How They Force Persistence |
|--------|---------------------------|
| Adam Kues | 6-hour floor + anti-convergence + "do not return merely because current approaches fail" |
| @mdp_sec | 5-phase pipeline where 83% of value is post-linear "focused weirdness" |
| @aituglo | Literally just "keep going" on a loop |

**The prompt tells the model HOW to think. The system keeps it RUNNING.**

---

## The Most Important Unspoken Takeaway

> **The prompts are almost irrelevant without a closed-loop environment that can act, remember, recover, and disprove.**

Every high-performing system spends the majority of its value on:

1. **Tooling** — browsers, accounts, OTP, MITM, CDP
2. **State** — sessions, cookies, ownership metadata, operation maps
3. **Memory** — prior findings, surface-matched patterns
4. **Validation** — adversarial review, reproduction, hostile triage
5. **Recovery** — handling failures, CAPTCHAs, session expiry

Publishing the prompt alone is theater. **The real moat is the research harness that keeps the model honest and productive for hours.**

---

## The 80/20 of AI Bug Bounty

| 20% (The Prompt) | 80% (The Harness) |
|------------------|-------------------|
| What to look for | Being able to look at all |
| How to test | Having the sessions/cookies/tokens to test with |
| How to exploit | Being able to verify the exploit works |
| How to write the report | Having screenshots from real execution |
| "Find IDORs" | Knowing who owns every object and who should access it |

---

## The New Problems (August 2026)

### 1. AI-Induced Duplicate Reports

@aituglo documented this: when multiple hunters point the same AI models at the same scope, everyone finds the same bugs. "Dupe land."

**Implication:** The edge is NOT in running AI on popular targets. It's in:
- Testing programs others aren't testing
- Going deeper than the AI's first pass
- Finding the bugs the AI missed, not the ones it found

### 2. Shrinking Low/Medium Bounties

CTBB Podcast discussion: programs are cutting low/medium payouts as AI makes those bugs easier to find. High payouts are moving behind VIP/private access.

**Implication:** AI raises the floor. You need to hunt above it — chain bugs, find business logic flaws, go for impact.

### 3. Model Refusal Friction

@medusa_0xf documented: Fable 5 silently rerouted security research prompts. Safety routers increasingly interfere with legitimate pentesting.

**Implication:** Know which models refuse. Have fallback models. Route security-sensitive work to models that don't block it.

### 4. AI Overconfidence in Internal Scanners

@s1r1u5_: companies think internal AI scanners replace bug bounty, but "researcher with taste + AI" still finds what scanners miss.

**Implication:** The value is researcher judgment + AI speed, not AI alone.

---

## What Separates the Top Performers

| Trait | Average Hunter | Top Performer |
|-------|---------------|---------------|
| AI Usage | "Find bugs in this app" | Multi-phase, multi-model, anti-convergence |
| Validation | Trusts AI output | Adversarial review, reproduction, hostile triage |
| State | Fresh session each time | Persistent sessions, ownership metadata, memory |
| Scope | Popular programs, same as everyone | Programs others skip, depth over breadth |
| Output | Reports individual bugs | Chains findings, escalates, maximizes impact |
| Learning | Each finding is standalone | Memory system — prior findings inform future hunts |

---

## The 7-Question Gate (from Claude-BugHunter)

Before submitting ANY AI-generated finding, answer:

1. Is this actually exploitable, not just misconfigured?
2. Does this affect real user data, money, or accounts — not just test data?
3. Is this 100% in scope per the program policy?
4. Would a reasonable program pay for this?
5. Do I have a complete, reproducible PoC with exact HTTP requests?
6. Have I ruled out false positive indicators (read-only, sandboxed, unexploitable)?
7. What is the realistic severity — not what I wish it was, what it actually is?

**If any answer is "no" or "not sure" — do not report. Keep digging.**

---

## The Three Pillars

Every production AI bug bounty system needs:

### Pillar 1: Persistence
> Something that prevents the model from stopping.

- Time floor (Adam Kues: 6 hours)
- Loop wrapper (@aituglo: "keep going")
- Multi-phase pipeline (@mdp_sec: 5 phases)

### Pillar 2: Validation
> Something that catches AI hallucinations before they become reports.

- Adversarial review (P10 hostile triager)
- Independent reproduction (P9 reproducer)
- Live verification (Adam Kues: test SQLi on real install)

### Pillar 3: Memory
> Something that prevents starting from zero every time.

- Prior findings surface-matched to current target (@mdp_sec: 241 findings)
- Operation maps that persist across sessions
- Session state that can be resumed

**If you have all three, you have a system. Missing any = you have a prompt and hope.**

---

## The Window Is Closing

The current advantage of AI + bug bounty won't last forever:

1. **Programs are adapting** — lower payouts, private programs, AI-specific scope rules
2. **Dupes are increasing** — more hunters using the same models on the same targets
3. **Defenders are using AI too** — internal AI scanners catch low-hanging fruit before bounty hunters arrive

**What remains durable:** Chaining bugs, finding business logic flaws, deep code audit of forgotten assets, acquisition targets with legacy code. AI is best at these, and they're the hardest for defenders to automate away.

**What's eroding:** Single-step IDORs, reflected XSS, basic auth issues, and any bug class where "just point AI at it" works for everyone.
