# AI Bug Bounty Research — August 2026

Curated research on how top security researchers use frontier AI models (GPT-5.6 Sol, Claude Opus 4.6/4.8, DeepSeek V4 Pro, Grok) for real bug bounty hunting.

**Research conducted:** August 6, 2026
**Sources:** X.com (Twitter), GitHub, security write-ups, CTBB Podcast

---

## What's Inside

| File | What You Get |
|------|-------------|
| [`01-creators.md`](./01-creators.md) | 15+ researchers profiled with post links, models used, methodology |
| [`02-prompts-and-techniques.md`](./02-prompts-and-techniques.md) | Verbatim prompts, reconstructed prompts, every technique worth stealing |
| [`03-systems-and-architecture.md`](./03-systems-and-architecture.md) | @mdp_sec's 5-phase pipeline, harness design, adversarial validation |
| [`04-models-and-tools.md`](./04-models-and-tools.md) | Model comparison table, GitHub repos, MCP configs, install commands |
| [`05-patterns-and-insights.md`](./05-patterns-and-insights.md) | Unifying principles, unspoken truths, what nobody is saying publicly |
| [`06-underdogs.md`](./06-underdogs.md) | Under-2000-follower researchers shipping original work |
| [`07-article-blueprint.md`](./07-article-blueprint.md) | Complete article structure with the Pass 4 synthesis prompt |
| [`prompts/`](./prompts/) | Verbatim prompt artifacts |
| [`tools/`](./tools/) | Copy-paste setup commands |

---

## The Core Thesis

> **The prompt is 5%. The harness is 95%.**
>
> Every high-performing AI bug bounty system spends 80%+ of its value on tooling, state management, and adversarial validation. The model finds leads. The harness proves them.
>
> Stop hunting for the magic prompt. Start building the system that keeps the model honest and running.

---

## Key Findings at a Glance

### The wp2shell Moment
Adam Kues used GPT-5.6 Sol Ultra with a research-grade prompt to find **pre-auth WordPress RCE** (2 new CVEs chained) in ~10 hours. Estimated exploit-broker value: **$500K**.

### The System
@mdp_sec built a 95% automated pipeline: **$104,238 in 166 days, 243 reports**. 100 isolated Chrome profiles, 5-phase testing, 3-stage adversarial validation. 83% of findings come from "focused weirdness" post-linear testing.

### The Model Consensus (August 2026)
- **Primary driver:** GPT-5.6 Sol / Codex (4 of 5 top creators)
- **Second eyes:** Claude Opus 4.6/4.8
- **Cost/speed:** DeepSeek V4 Flash (~10¢/day), Grok (recon)
- **Harness:** Claude Code or Codex CLI (symlink skills between both)

### The Unspoken Truth
Nobody publishing AI bug bounty content shares their actual prompts because **the prompts are the least interesting part.** The real moat is the closed-loop environment: browsers, accounts, OTP retrieval, memory, evidence capture, and hostile self-triage.

---

## How to Use This Repo

1. **Read in order** — 01 → 02 → 03 → 04. Each builds on the last.
2. **Copy the prompts** from `prompts/` — they're verbatim where available, reconstructed where not.
3. **Run the commands** from `tools/setup-commands.md` — get tooling installed today.
4. **Follow the roadmap** in `07-article-blueprint.md` Section 7 — leveled build guide from "tonight" to "moat."
5. **Write your article** using the blueprint in `07-article-blueprint.md`.

---

## Quick Start

```bash
# Level 1 — Hunt tonight
git clone https://github.com/elementalsouls/Claude-BugHunter.git
claude mcp add burp --transport sse --url http://127.0.0.1:9876/

# Symlink skills across harnesses (via @rez0__)
ln -s ~/.claude/claude.md ~/.codex/agent.md
ln -s ~/.claude/skills ~/.codex/skills
```

---

## Credit

All techniques and prompts attributed to their creators via X handles and post links. See individual files for attribution. This repo is research aggregation + curation — original sources linked throughout.

## License

Research purposes. Prompts belong to their original authors. Attribute accordingly.
