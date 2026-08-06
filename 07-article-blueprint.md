# 07 — Article Blueprint

Complete structure for your X.com article / blog post on AI-powered bug bounty hunting (August 2026).

---

## Title Options (Ranked)

1. **"The Prompts Are the Least Interesting Part: How AI Actually Finds Bugs in 2026"**
   - Why: @mdp_sec quote as title. Signals contrarian take. Promises insider knowledge.

2. **"GPT-5.6 Found a $500K WordPress Zero-Day. Here's the Prompt."**
   - Why: Specific model. Specific result. Specific dollar figure. Implies you have the prompt (which you do — verbatim).

3. **"The AI Bug Bounty Stack: What Top Hunters Actually Use (It's Not What You Think)"**
   - Why: Practical. Actionable. The "not what you think" hook works.

4. **"I Analyzed 20 Bug Hunters Using AI. Here's What the Best Ones Do Differently."**
   - Why: Credibility through research. Comparison angle. Promise of insider patterns.

5. **"Stop Asking for the Prompt. Build the Harness."**
   - Why: Short. Punchy. Controversial. Direct quote energy.

6. **"83% of AI-Found Bugs Come From 'Weirdness,' Not Checklists"**
   - Why: Specific stat. Counterintuitive. Makes people click to understand.

7. **"The $104K AI Bug Bounty System (That No One Will Show You)"**
   - Why: @mdp_sec's numbers. Exclusivity angle. High dollar figure.

**My pick for X.com:** #2 for reach, #1 for credibility, #5 for impact.

---

## Article Structure

---

### SECTION 1 — The State of AI Bug Bounty (400 words)

**Lead with the wp2shell moment.**

In July 2026, Adam Kues pointed GPT-5.6 Sol Ultra at a fresh clone of WordPress. He gave it a research-grade prompt with anti-convergence heuristics, a 6-hour minimum time floor, and one concrete goal: `read /flag` from the root filesystem.

~10 hours later, the model had found pre-auth SQLi — and chained it into full remote code execution on default WordPress. Two new CVEs. Exploit broker value: ~$500K.

This changed the conversation. AI went from "helps write your reports" to "finds the bugs."

**The model stack has consolidated.**

As of August 2026, the consensus among top hunters is clear: GPT-5.6 Sol / Codex is the primary driver. Claude Opus is now "2nd eyes" — valuable for validation, not autonomous hunting. DeepSeek V4 Flash handles cost-sensitive volume. Grok does recon.

Multiple top hunters independently abandoned Claude as their primary model this summer. @aituglo: "Claude is getting worse… it doesn't want to work… GPT keeps going without flinching." @rez0__: "codex is cracked."

**The numbers are real.**

@mdp_sec built a 95% automated pipeline: $104,238 in 166 days, 243 reports. @ClovisMint earned $130K+ from vulnerabilities IN AI products — prompt injection → ATO on Meta AI systems.

**But there are new problems.**

AI convergence means duplicate reports on popular targets. Programs are cutting low/medium bounties. VIP/private access is gating high payouts. The window for "just point AI at a target" is closing.

---

### SECTION 2 — Anatomy of a $500K Prompt (700 words)

**This is the centerpiece.** Reproduce Adam Kues' full wp2shell prompt VERBATIM, then break down each technique.

[See `prompts/wp2shell-verbatim.md` for the complete prompt text]

**Technique breakdown:**

1. **Anti-convergence registry** — groups agents by research idea, throttles dominant approaches, redirects to underexplored areas
2. **Diverse portfolio + explicit surface list** — names 10+ attack surfaces, demands multiple incompatible routes kept alive
3. **No git history, no internet** — forces first-principles analysis, prevents "cheating" via public CVEs
4. **6-hour minimum + anti-early-exit** — overrides the #1 AI failure mode: giving up after 1-2 hours
5. **Concrete win condition** — `read /flag` not "find bugs"
6. **Root agent synthesis loop** — active research management, not passive analysis
7. **Adversarial double-check** — every finding sanity-checked before acceptance

**What it found:**

CVE-2026-63030 (batch endpoint desync) + CVE-2026-60137 (author__not_in SQLi) → recursive batch → cache poisoning → changeset admin → plugin install → pre-auth RCE. Default WordPress 6.9.x / 7.0.x.

---

### SECTION 3 — The System, Not the Prompt (500 words)

@mdp_sec's direct quote: "People keep asking me for the prompt behind my AI bug bounty system. There isn't one. I could give you every prompt today and you still would not have my system."

**The 5-phase pipeline:**
- Map → operation list, not URLs
- Access → accounts, OTP, ownership metadata
- Broad Test → every operation tagged
- **Focused Weirdness** → 83% of findings originate here
- Adversarial Validation → P8 (validate) → P9 (reproduce) → P10 (hostile triage)

**Infrastructure:** 3,636 programs. 100 Chrome profiles. Geo-split. OTP retrieval. 241 finding memory. ~$209K API cost.

**Thesis:** The prompt is 5%. The harness — browsers, accounts, traffic, memory, evidence, validation — is 95%.

---

### SECTION 4 — The Prompt Vault (500 words)

Every technique worth stealing:

1. **The "Keep Going" Loop** (@aituglo) — simplest entry point. Model produces 50 leads, you triage to 1-2.
2. **Model Routing** (@mdp_sec) — Codex drives, Claude reviews, Grok recons.
3. **Symlink Multi-Platform** (@rez0__) — `ln -s ~/.claude/claude.md ~/.codex/agent.md`
4. **Cost-Optimized Stack** (@lostsec_ + @elkrispis) — Claude Code + DeepSeek V4 Flash, ~10¢/day
5. **Focused Weirdness Prompt** (reconstructed) — the prompt where 83% of findings originate
6. **Skill Pack + MCP Ecosystem** — Claude-BugHunter + Burp MCP + Caido MCP

---

### SECTION 5 — Underdogs Worth Following (250 words)

Profile: @horizonfps (103-tool MCP), @nice_hacker_ (BAC/PII via redmind), @elkrispis (10¢/day DeepSeek), @hieund1994 (~30 followers, raw learning curve).

[See `06-underdogs.md` for full profiles]

---

### SECTION 6 — Models Compared (250 words)

Quick reference table + the Claude → Codex shift story.

[See `04-models-and-tools.md` for the full table]

---

### SECTION 7 — Build Your Own System (350 words)

Leveled roadmap: Tonight → This Week → This Month → This Quarter → Moat.

[See `tools/setup-commands.md` for copy-paste install commands]

---

### SECTION 8 — The Unspoken Truth (150 words)

Nobody publishing AI bug bounty content will say this explicitly:

**The prompt is theater. The harness is the game.**

Every high-performing system spends 80%+ of its value on tooling, state management, and adversarial validation. The model finds leads. The harness proves them.

Stop hunting for the magic prompt. Start building the system that keeps the model honest and running.

---

## What Makes This Article Different

1. **Verbatim prompt from a $500K find** — nobody else has broken this down
2. **The "harness not prompt" thesis** — contrarian, backed by data, memorable
3. **Underdog profiles** — creators nobody else is covering
4. **Actionable roadmap** — reader can hunt tonight after reading
5. **Specific model recommendations** — not "AI is useful" but "use GPT-5.6 Sol for this, DeepSeek for that"

---

## Before You Publish

1. **DM Coffin (@lostsec_)** — get one exclusive prompt. This is your differentiator.
2. **Test the Adam Kues prompt structure** on one of your own targets. Include your results in Section 2 as a "I tried this myself" sidebar.
3. **Screenshot your Claude Code setup** — readers want to see what a real hunting environment looks like.
4. **Run Pass 4 in Grok** — use the synthesized draft as your first pass, then rewrite in your voice.
5. **Include your own findings** — the article is 10x stronger if you tested these techniques and can say "here's what I found."
