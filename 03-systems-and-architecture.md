# 03 — Systems & Architecture

How top hunters structure their AI systems. The prompt is 5%. This is the other 95%.

---

## @mdp_sec — The 5-Phase Pipeline

**Source:** https://x.com/mdp_sec/status/2085187655101530370
**Stats:** 243 reports, $104,238 in 166 days, ~95% automated

### System Overview

```
DASHBOARD (3,636 programs)
    │
    ▼
PHASE 1: MAP ─── AI builds operation list
    │
    ▼
PHASE 2: ACCESS ─── AI creates accounts, reads OTP, completes signup
    │
    ▼
PHASE 3: BROAD TEST ─── Every operation tested, outcome recorded
    │
    ▼
PHASE 4: FOCUSED WEIRDNESS ─── 83% of findings originate here ⭐
    │
    ▼
PHASE 5: ADVERSARIAL VALIDATION ─── P8 → P9 → P10
    │
    ▼
REPORT / SUBMIT
```

### Phase 1 — Map

AI builds a list of **operations**, not URLs:
- Hosts and services
- JavaScript bundles and API endpoints
- GraphQL queries and mutations
- Authentication flows and session management
- Business functions (what can users actually DO?)
- Browser routes and client-side state
- Exposed configuration and error messages

**Output:** A structured attack surface map, not a URL list.

### Phase 2 — Access

AI handles account lifecycle:
- Creates test accounts using unique email addresses
- Reads verification emails and pulls OTP codes
- Completes signup flows and creates initial resources
- For access-control testing: creates attacker + victim accounts
- Records which request created each object, who owns it, who should be allowed to access it

### Phase 3 — Broad Test

Checklist phase. Every operation gets a recorded outcome:
- Access control (horizontal + vertical)
- Authentication and session management
- SSRF vectors
- File upload paths
- GraphQL authorization
- Business logic boundaries
- Client-side behavior
- Injection surfaces

**Every operation tagged:** `tested | blocked | excluded | not applicable`

**Key insight:** Only ~17% of submitted reports started in these linear phases.

### Phase 4 — Focused Weirdness ⭐

> "After the broad testing, focused models go back through the target and follow anything that looks strange. This is where most of the real findings come from."

**83% of findings originate here.**

The model re-examines every anomalous or incomplete behavior from the map and broad phase. Follows the weird until it understands:
- Why the system allows it
- What the real impact is
- Whether it chains into something bigger

See [`prompts/focused-weirdness-reconstructed.md`](./prompts/focused-weirdness-reconstructed.md) for the reconstructed prompt.

### Phase 5 — Adversarial Validation (P8/P9/P10)

Three-stage gate before any report is submitted:

| Stage | Role | Behavior |
|-------|------|----------|
| **P8** | Validator | Validates finding + tries every safe escalation path |
| **P9** | Independent reproducer | Reproduces from scratch, fixes proof, checks screenshots |
| **P10** | Hostile triager | Does NOT believe the report. Re-runs every step. Can pass, downgrade, or reject. Cannot invent angles to save weak reports. |

---

## Infrastructure

### Browser Farm
- **100 isolated Chrome profiles** (full Chrome — own cookies, storage, proxy, geo, traffic capture, CAPTCHA support)
- **Geo-split:** 50 US / 20 UK / 20 AU / 10 Singapore
- **Persistent:** AI can return to the same logged-in session
- **VNC access:** For manual MFA/CAPTCHA when needed

### Traffic Capture
- CDP (Chrome DevTools Protocol) for browser driving
- MITM proxy for all traffic monitoring
- Every request/response captured for evidence

### Memory System
- **241 validated findings** stored
- **Surface-matched retrieval** — matches current target to prior finding patterns
- Not dumped wholesale — hints, not templates
- Prevents duplicate work across targets

### Program Dashboard
- **3,636 program records**
- Tracks: scope, exclusions, rules, reward ranges, history, scope changes
- AI pulls context before starting any test
- Human still manually chooses which programs to test (~80% of completed targets produced no report)

### Cost
- **288.1B tokens** consumed
- **~$209K equivalent** API cost
- Mostly covered by subscriptions (max-tier Codex + Claude)

---

## Key Design Principles

### 1. State Persistence
The AI must be able to return to the same session, same cookies, same state. Without this, you can't chain findings or escalate.

### 2. Ownership Metadata
Every created object tracks: who created it, who owns it, who should be allowed to access it. This is how the AI tests IDORs — it already knows the access matrix.

### 3. Recorded Outcomes
No operation is left "maybe." Everything gets tagged. This prevents the AI from skipping hard-to-test surfaces and ensures completeness.

### 4. Adversarial Gate
P10 is the killer feature. A hostile triager that tries to KILL every finding before submission. Most AI findings are hallucinated or overestimated. The gate catches them.

### 5. Focused Weirdness Over Checklist
The linear phases only produce ~17% of findings. The real value is in the post-linear "that's weird" exploration. The checklist builds the map. The weirdness finds the gold.

---

## @aituglo — The Simplest System That Works

```
while True:
    AI.hunt(target)     # Run Claude/Codex on one target
    leads.append(results)
    if human_tired:
        triage(leads)   # 50 leads → 1-2 real bugs
```

**Infrastructure:** Just a server + SSH + tmux. No browser farm. No OTP retrieval. No dashboard.

**Result:** Works. Produces real leads. But requires heavy human triage and has a high dupe rate.

**Evolution:** Started with Claude → switched to Codex/OpenAI because Claude refused to continue running.

---

## Adam Kues — Single Target, Maximum Depth

```
1. Clone target (WordPress, stripped .git)
2. Write research-grade prompt with anti-convergence + time floor
3. Point GPT-5.6 Sol at it with 4 parallel agents
4. Wait 10+ hours
5. Verify findings on live install
6. Ask model to escalate SQLi → RCE
```

**Infrastructure:** Minimal. No browser profiles. No account management. One target, one prompt, deep focus.

**Result:** The most impressive single AI-assisted vulnerability find of 2026.

---

## Architecture Comparison

| Dimension | @mdp_sec | @aituglo | Adam Kues |
|-----------|----------|----------|-----------|
| Targets | Many (3,636 programs) | Few at a time | One |
| Depth | Medium (focused weirdness) | Shallow (loop + triage) | Maximum (6+ hours) |
| Automation | 95% | ~50% | ~80% |
| Infrastructure | Massive (100 profiles, MITM, memory) | Minimal (server + tmux) | Minimal (Codex sub) |
| Validation | 3-stage adversarial | Human triage | Live verification |
| Cost | ~$209K (subsidized) | Low | ~$25/run |
| Best for | Volume + consistency | Learning + quick wins | Deep research / zero-days |

---

## The Meta-Pattern

Every high-performing system has these three components:

1. **Something that forces persistence** — time floor, loop, multi-phase pipeline. Don't let the AI stop.
2. **Something that validates findings** — adversarial review, reproduction, hostile triage. Don't trust the AI.
3. **Something that remembers** — prior findings, operation maps, session state. Don't make the AI start fresh.

**If you have all three, you have a system. If you're missing any, you have a prompt and hope.**
