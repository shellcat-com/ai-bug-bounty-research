# Setup Commands — Copy-Paste Ready

Everything you need to install and configure for AI-powered bug bounty hunting.

---

## Level 1 — Hunt Tonight

### Install Claude-BugHunter Skill Pack
```bash
git clone https://github.com/elementalsouls/Claude-BugHunter.git ~/Claude-BugHunter
# 82 skills, 15 slash commands, 681 report patterns, 24 vuln classes
```

### Add Burp MCP (if using Burp Suite)
```bash
# Prerequisite: Install "MCP Server" extension from Burp BApp Store
# Then connect Claude Code to Burp:
claude mcp add burp --transport sse --url http://127.0.0.1:9876/
```

### Add Caido MCP (if using Caido)
```bash
git clone https://github.com/c0tton-fluff/caido-mcp-server.git
# 66 tools, GraphQL → Caido integration
```

### Start Hunting
```bash
# In Claude Code:
/recon    # Map the target
/hunt     # Hunt for vulnerabilities
/report   # Generate report
```

---

## Level 2 — Multi-Platform (This Week)

### Symlink Skills Across All Harnesses (@rez0__ trick)
```bash
# Works for: Claude Code, Codex CLI, OpenCode, Hermes Agent
ln -s ~/.claude/claude.md ~/.codex/agent.md
ln -s ~/.claude/skills ~/.codex/skills
```

### Install Other Skill Packs
```bash
# shuvonsec pack (includes MCP clients)
git clone https://github.com/shuvonsec/claude-bug-bounty.git

# redmind (proven — found paid BAC/PII on major auto program)
git clone https://github.com/Rifteo/skills.git

# Claude-OSINT (90+ recon modules)
git clone https://github.com/elementalsouls/Claude-OSINT.git

# Bug Bounty Agents (persona-based)
git clone https://github.com/matty69v/Bug-Bounty-Agents.git
```

### Set Up DeepSeek V4 Flash (Cost-Optimized)
```bash
# Use DeepSeek for volume phases, Claude for validation only
# @elkrispis: "intensive all-day use for ~10 cents"
# Full walkthrough on @lostsec_'s YouTube channel
```

---

## Level 3 — Build the Harness (This Month)

### Browser Automation
```bash
# Playwright MCP for browser-driven testing
# Route traffic through proxy (Burp/Caido)

# Key capabilities needed:
# - Multiple isolated browser profiles
# - Per-profile cookies, storage, proxy, geo
# - Traffic capture (MITM)
# - CAPTCHA handling (manual fallback via VNC)
```

### Account Management
```bash
# You need:
# - Unique email addresses per test account
# - OTP/verification email reading
# - Automated signup flow completion
# - State persistence (return to same logged-in session)
# - Ownership metadata tracking (who created what, who should access it)
```

### Memory System
```bash
# Track:
# - Prior findings (surface-matched, not dumped wholesale)
# - Operation maps per target
# - Test outcomes per operation
# - Gadgets and patterns that repeat across targets
```

---

## Level 4 — Adversarial Validation (This Quarter)

### P8 — Validate + Escalate
```bash
# Prompt your AI reviewer:
# "Validate this finding. Try every safe escalation path.
#  Record what worked and the maximum impact achieved."
```

### P9 — Independent Reproduction
```bash
# Prompt your AI reproducer:
# "Reproduce this finding from scratch using ONLY the trigger
#  condition and prerequisites described. Fix any incorrect steps.
#  Verify all screenshots. If you cannot reproduce, flag it."
```

### P10 — Hostile Triager
```bash
# Prompt your AI triager:
# "You do NOT believe this report is real. Re-run every step.
#  Check every prerequisite. Verify severity. Verify platform.
#  You may pass, block for evidence, downgrade, or reject.
#  You may NOT invent new angles to save a weak report.
#  Every screenshot must come from real execution."
```

---

## Model Configuration Reference

### Primary Driver: GPT-5.6 Sol / Codex
```bash
# For: deep code audit, multi-agent chains, long autonomous runs
# Subscription: Codex Max or ChatGPT Pro/Enterprise ($200/mo)
# Best at: sustained agentic work, low refusal rate
# Used by: @mdp_sec, @rez0__, @aituglo, Adam Kues
```

### Reviewer: Claude Opus 4.6/4.8
```bash
# For: validation, structured reasoning, hallucination detection
# Subscription: Claude Max ($20-200/mo)
# Best at: catching errors, reviewing reports, "2nd eyes"
# Used by: @mdp_sec (secondary role)
```

### Cost Volume: DeepSeek V4 Flash
```bash
# For: recon, broad testing, cost-sensitive phases
# Cost: ~$3/mo for all-day use
# Best at: volume tasks where correctness isn't critical
# Used by: @lostsec_, @elkrispis
```

### Recon Speed: Grok
```bash
# For: fast browser driving, quick recon passes
# Cost: Included in X Premium
# Best at: speed
# Used by: @mdp_sec (recon/browser role)
```

---

## Quick Diagnostic Commands

```bash
# Check current Claude Code config
cat ~/.claude/claude.md
cat ~/.claude/settings.json

# List installed MCP servers
claude mcp list

# Check git repos for skill packs
ls ~/Claude-BugHunter/ 2>/dev/null
ls ~/claude-bug-bounty/ 2>/dev/null

# Test Burp MCP connection
curl -s http://127.0.0.1:9876/health 2>/dev/null || echo "Burp MCP not running"

# Check symlinks
ls -la ~/.codex/agent.md 2>/dev/null
ls -la ~/.codex/skills 2>/dev/null
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Claude refuses to do security testing | Route to Codex/GPT-5.6. Claude increasingly refuses autonomous hunting. Use Claude only for validation. |
| Model stops after 1-2 hours | Add time floor to prompt. Wrap in "keep going" loop. Switch to Codex — it doesn't "get tired." |
| Too many false positives | Add adversarial validation. Don't submit without P8/P9/P10 gate. |
| Duplicate reports on popular targets | Hunt less popular programs. Go deeper than AI's first pass. Find what AI misses. |
| High API costs | Route volume phases to DeepSeek V4 Flash (~10¢/day). Reserve Codex/Claude for validation only. |
| MCP connection fails | Verify Burp MCP Server extension is running. Check port. Restart Claude Code. |
