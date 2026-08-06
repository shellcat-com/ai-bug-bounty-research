# 01 — Creators & Post Library

Every researcher profiled, ranked by signal strength. Prioritized June–August 2026.

---

## Tier 1 — Proven Bounties + Verifiable Methodology

### @mdp_sec — Marius du Preez

- **Followers:** ~1.4k
- **Status:** UNDERDOG with the most detailed system on X
- **Models:** Codex (driver) + Claude Opus 4.6/4.8 (2nd eyes) + Grok (recon/browser)
- **Key post:** https://x.com/mdp_sec/status/2085187655101530370 (Aug 6, 2026)
- **Stats:** 243 reports / **$104,238 in 166 days** / ~95% automated / 3,636 program records / 100 isolated Chrome profiles
- **Methodology:** Full research environment, not just prompts. Dashboard → Map → Access → Broad Test → Focused Weirdness → Adversarial Validation (P8/P9/P10). AI handles recon, account creation, testing, PoC evidence, and report packaging. Human selects targets and does final review.
- **The quote:** "People keep asking me for the prompt behind my AI bug bounty system. I think they are expecting one huge prompt they can paste into Claude or Codex. There isn't one. I could give you every prompt today and you still would not have my system."
- **83% of findings** come from "focused weirdness" post-linear testing, NOT from the checklist phases.

### @ClovisMint — Minty Fresh Racc

- **Followers:** ~8.4k
- **Key post:** https://x.com/ClovisMint/status/2084666858373046408 (Aug 4, 2026)
- **Stats:** **$130K+ total bounties** from Meta AI vulnerabilities
- **Angle:** Finds vulnerabilities IN AI products — prompt injection → ATO. DEF CON workshop with @NahamSec.
- **Methodology:** Thinking about systems with agentic capabilities + hands-on case studies from Meta findings.

### CTBB Podcast — @ctbbpodcast (hosts @Rhynorater, @rez0__, @gr3pme)

- **Key post:** https://x.com/ctbbpodcast/status/2085305633683746915 (Aug 6, 2026)
- **Signal:** Covered the wp2shell story — GPT-5.6 Sol found pre-auth WordPress RCE chain in ~10 hours
- **Write-up:** https://blog.criticalthinkingpodcast.io/p/hackernotes-ep-186-is-gpt-5-6-sol-superhuman-wp2shell-rails-rce-and-the-shrinking-bounty-table
- **Impact:** "No human could have done it in that window." Discussion on shrinking low/medium bounties blamed on AI.

---

## Tier 2 — Real Methodology, Less Proven Bounty Data

### @lostsec_ — Coffin

- **Followers:** ~30k
- **Key posts:**
  - https://x.com/lostsec_/status/2085025382827483613 (Aug 5, 2026) — Claude Code + DeepSeek V4 Flash setup guide
  - https://x.com/lostsec_/status/2082654683701870983 — Claude Pro mastery for hunting workflows
- **Methodology:** Practical tooling tutorials. Wires Claude Code with cheap DeepSeek for real tasks. Emphasizes configuration and training the approach. YouTube walkthrough for full setup.
- **Note:** YOU KNOW HIM. DM for exclusive prompt content — this would set your article apart.

### @aituglo — Cassim

- **Followers:** ~2k
- **Key posts:**
  - https://x.com/aituglo/status/2084913548010955061 (Aug 5) — Stopped using Claude; better options now
  - https://x.com/aituglo/status/2074766687770128521 (Jul 8) — "keep going" loop + triage 50 AI findings → 1-2 leads
  - https://x.com/aituglo/status/2069756021153714331 — Group hunting with Claude → everyone found same bugs (dupe problem)
- **Methodology:** Runs Claude in long loops, then human triages heavily. Most honest about pain points: dupes, model switching costs, triage overhead.
- **The quote:** "I realized I've been using Claude wrong for months. I just told it 'keep going' on a loop and triaged the 50 bugs it threw at me to keep 1 or 2 potential leads. You'd never manage a real intern that way."
- **Switch:** Abandoned Claude for Codex/OpenAI — "Claude is getting worse… it doesn't want to work… GPT keeps going without flinching."
- **Weekly newsletter:** https://aituglo.com/

### @medusa_0xf — Medusa

- **Followers:** ~9k
- **Key post:** https://x.com/medusa_0xf/status/2065090767736218045 (Jun 11, 2026)
- **Methodology:** Uses Claude for actual research. Documents refusal/safety-router friction for legitimate pentesting. Shares recon + exploit walkthroughs. Pairs AI discussion with real findings.
- **Angle:** Only creator documenting model limitations/refusals for security research. Important counterpoint.

---

## Tier 3 — Signal, But Weaker

### @Rhynorater — Justin Gardner

- **Followers:** ~38k
- **Key post:** Referenced in https://x.com/yeswehack/status/2084625903460499578 (Aug 4, 2026)
- **Methodology:** AI removes friction but doesn't replace hunter judgment. Custom skills + agents accelerate finding high-impact bugs on top of deep domain knowledge. CTBB Podcast co-host.
- **Issue:** No shared prompts, custom skills, or agent configs. High-level only.

### @rez0__ — Joseph Thacker

- **Followers:** ~73k
- **Key posts:**
  - https://x.com/rez0__/status/2081039330487767143 — Claude Code as harness; Codex/Hermes for hackbots
  - https://x.com/rez0__/status/2083256074279211500 — "just use ai to find bugs now while you can"
- **Key contribution:** Symlink trick — `ln -s ~/.claude/claude.md ~/.codex/agent.md` and skills folders
- **The quote:** "okay im calling it officially. codex is cracked. if you're a bb hunter and you dont have a hackbot set up yet, i recommend codex with gpt5.5 over claude code."
- **Issue:** No shared prompts or full agent configs.

### @S1r1u5_

- **Key posts:**
  - https://x.com/S1r1u5_/status/2083154341326733705 — AI-induced overconfidence in internal scanners vs. real hunters
  - https://x.com/S1r1u5_/status/2083651999116013667 — GPT-5.6 Sol superiority commentary
- **Methodology:** Critiques over-reliance on AI scanners. Emphasizes "researcher with taste + AI."
- **Issue:** Meta-commentary only. No specific prompts or techniques. Good for quotes, not methods.

### @arshadkazmi42 — Arshad Kazmi

- **Followers:** ~3k
- **Key post:** https://x.com/arshadkazmi42/status/2083620847395483660 (Aug 1, 2026)
- **Methodology:** Pivoted product to bug-bounty-first agent. Claude Code runs hours autonomously with findings dashboard. Already finding low-hanging fruit.
- **Issue:** Building product. No bounty numbers yet. Watch, don't cite.

---

## Tier 4 — Single-Signal Mentions

| Creator | What They Shared |
|---------|-----------------|
| @QCXINT_ | Free-LLM agent earned $100 crypto bounty in ~2 hours |
| @harshad_hacker | AI Recon + 403 Bypass Burp extension (older content) |
| @serros404 | Hermes Agent + DeepSeek in Brazilian bug bounty circles |
| @Kitsuneagentlab | Praises Hermes agent for bug hunting |

---

## The wp2shell Author — Adam Kues (@hash_kitten)

Not primarily a bug bounty content creator, but produced the single most valuable AI+security prompt artifact of 2026.

- **Write-up:** https://slcyber.io/research-center/exploit-brokers-pay-500000-for-a-wordpress-rce-i-found-one-with-gpt5-6/
- **Model:** GPT-5.6 Sol Ultra (ChatGPT Work Pro / Enterprise / Codex Plus)
- **Result:** Pre-auth WordPress RCE (2 new CVEs) in ~10 hours, ~$25 pro-rata API cost
- **Vulns found:**
  - CVE-2026-63030: REST API batch endpoint validation/execution desync
  - CVE-2026-60137: SQLi in `WP_Query` `author__not_in` parameter
  - Chained: recursive batch → cache poisoning → changeset admin → plugin install → RCE
- **Estimated broker value:** ~$500K

---

## Coverage Map

| Angle | Strongest Sources |
|-------|------------------|
| AI for recon (JS, endpoints, subdomains) | @mdp_sec, Claude-BugHunter skills, @lostsec_ |
| Code review / vuln discovery | @mdp_sec focused cycles, Claude-BugHunter patterns, @aituglo loop+triage |
| Write exploits / PoCs | Adam Kues wp2shell, @mdp_sec evidence/PoC generation |
| Full workflow automation | @mdp_sec (95%), Claude Code + agents (@Rhynorater, @rez0__, @arshadkazmi42, @lostsec_) |
| Sharing actual prompts | Adam Kues (verbatim), @mdp_sec (system-level only), @aituglo (usage notes) |
| Bounties earned with AI | @mdp_sec ($104K), @ClovisMint ($130K+), @QCXINT_ ($100) |
