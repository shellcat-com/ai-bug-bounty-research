# Focused Weirdness Prompt — Reconstructed

**Original concept:** @mdp_sec
**Source post:** https://x.com/mdp_sec/status/2085187655101530370
**Status:** RECONSTRUCTED — NOT confirmed by @mdp_sec. Reverse-engineered from his system description.
**Context:** 83% of his 243 submitted reports originated from "focused weirdness" cycles, not the linear testing phases.

---

## Reconstructed Prompt

```
You are in the focused-weirdness phase on target [TARGET].

Context already available:
- Full operation map (hosts, APIs, GraphQL, auth flows, business functions, browser routes)
- Live authenticated sessions (attacker + victim accounts) with ownership metadata for every created object
- Results of broad testing phase (every operation tagged tested/blocked/excluded/n/a)
- Retrieved patterns from prior validated findings that match this surface

Your only job is to re-examine every anomalous or incomplete behavior from the map and broad phase.
Do not re-run the entire linear checklist. Follow anything that looks strange, inconsistent, or only partially explained.

For each candidate:
1. Reproduce the observed weirdness from a realistic attacker position using the existing sessions.
2. Determine the exact condition that allows it (missing check, race, trust boundary, type confusion, business-logic assumption, etc.).
3. Escalate safely along every path that stays in scope until impact is proven or disproven.
4. Record: trigger, root cause, prerequisites, impact ceiling, control tests that failed/passed, and whether this is a security issue or intended product behavior.
5. If impact is unclear, spawn a short adversarial sub-check that tries to disprove it before accepting it.

Use surface-matched prior findings only as hints, never as templates to force-fit.
Stop only when every weird observation has a recorded outcome (confirmed finding, false positive, or "needs human").
Prefer depth on the strangest behaviors over breadth.
```

---

## Why This Prompt Works

Based on @mdp_sec's description, the key elements are:

1. **Prerequisite context already exists** — the map and broad test phases built the foundation. This prompt assumes the AI already knows the target's attack surface and has active sessions. Without this context, the prompt is useless. This is WHY he says "I could give you every prompt today and you still would not have my system."

2. **"Follow anything that looks strange"** — this is the opposite of a checklist. It's curiosity-driven. The AI isn't checking off boxes — it's pursuing anomalies.

3. **Exact condition, not vague observation** — "not 'auth is broken' but 'the middleware checks req.user.id but the handler reads req.body.user_id'". Forces precision.

4. **Escalate until impact is either proven or disproven** — no "this might be vulnerable." Binary outcome: proven impact OR confirmed false positive OR "needs human."

5. **Spawn adversarial sub-checks** — the AI tries to DISPROVE its own conclusion before accepting it. Self-skepticism built into the prompt.

6. **Recorded outcomes for everything** — no loose ends. Every anomaly gets a final status.

7. **"Prior findings as hints, not templates"** — prevents pattern-matching past bugs onto new targets. The AI must find the actual bug, not a lookalike.

---

## How @mdp_sec Describes This Phase (Direct Quotes)

> "After the broad testing, focused models go back through the target and follow anything that looks strange. This is where most of the real findings come from."

> "Of 100 submitted reports he traced, only ~17% started in the linear phases; ~83% came from focused cycles or manual follow-up."

> "The models follow the weird behavior until they understand why the system allows it and what the real impact is."

---

## How to Use This

**You CANNOT use this prompt in isolation.** It requires:

1. An operation map (from a prior mapping phase)
2. Live authenticated browser sessions
3. Ownership metadata for created objects
4. Results from a broad test phase (tested/blocked/excluded/n/a tags)
5. A memory store of prior findings

**What you CAN do:**

1. Run a manual or AI-assisted mapping phase first
2. Run a broad test phase to tag all operations
3. THEN run this prompt with the context attached

Or, simpler version for getting started:

```
You are hunting on [TARGET]. You already know the API endpoints, auth flow, and business functions.

Your job: re-examine every behavior that seems even slightly off.

For anything weird:
1. Reproduce it
2. Find the exact code-level reason it works
3. Escalate until you prove impact or prove it's harmless
4. Try to DISPROVE your own conclusion before accepting it

Do not run a checklist. Follow the weird. Go deep on the strange stuff.
```

This stripped-down version won't produce @mdp_sec-level results, but it's a starting point.
