# 04 — Models & Tools

What to use, when to use it, and how to set it up.

---

## Model Consensus (August 2026)

### The Stack

```
PRIMARY DRIVER:     GPT-5.6 Sol / Codex        ← 4 of 5 top creators
SECONDARY REVIEW:   Claude Opus 4.6/4.8         ← "2nd eyes" role
RECON / SPEED:      Grok                        ← Browser driving, fast scanning
COST VOLUME:        DeepSeek V4 Flash           ← ~10 cents/day for heavy use
HARNESS:            Claude Code OR Codex CLI    ← Symlink skills between both
```

### The Shift: Claude → Codex (Summer 2026)

Multiple top hunters independently converged on the same conclusion:

| Creator | Quote |
|---------|-------|
| @mdp_sec | "codex is the driver. claude is 2nd eyes." |
| @rez0__ | "okay im calling it officially. codex is cracked." |
| @aituglo | "Claude is getting worse… it doesn't want to work… GPT keeps going without flinching." |
| @elkrispis | "OpenCode + DeepSeek Flash 4 completely destroys my Claude Code setup." |

**The pattern:** Claude refuses too much for long-running autonomous work. Codex/GPT-5.6 keeps going. Claude is still valuable as a structured reviewer — it catches hallucinations well.

---

## Model Comparison Table

| Use Case | Model | Why | Cost |
|----------|-------|-----|------|
| Deep code audit, multi-agent chains | GPT-5.6 Sol Ultra / Codex | Sustained multi-agent, low refusal rate, anti-convergence capable | $200/mo (Pro/Enterprise) |
| Validation, "2nd eyes" | Claude Opus 4.6/4.8 | Structured reasoning, hallucination detection, report quality | $20-200/mo |
| Cost-sensitive volume, fast recon | DeepSeek V4 Flash | ~10¢/day for all-day use | ~$3/mo |
| Browser driving, recon speed | Grok | Speed — "speedy af" per @mdp_sec | Included in X Premium |
| Harness (MCP/skills ecosystem) | Claude Code | Best MCP + skills ecosystem, Burp/Caido integration | Free + API |
| Harness (agentic long runs) | Codex CLI | Better for long-horizon autonomous work | Free + API |

---

## GitHub Repos & Skill Packs

### Primary

| Repo | Description | Stars |
|------|-------------|-------|
| [elementalsouls/Claude-BugHunter](https://github.com/elementalsouls/Claude-BugHunter) | 82 skills + 15 slash commands + 681 report patterns across 24 vuln classes | ~3K+ |
| [shuvonsec/claude-bug-bounty](https://github.com/shuvonsec/claude-bug-bounty) | Claude skills + MCP clients | — |
| [Rifteo/skills (redmind)](https://github.com/Rifteo/skills/tree/main/redmind) | AI skill that found a paid BAC/PII on major auto program | — |

### Supporting

| Repo | Description |
|------|-------------|
| [elementalsouls/Claude-OSINT](https://github.com/elementalsouls/Claude-OSINT) | 90+ recon modules |
| [matty69v/Bug-Bounty-Agents](https://github.com/matty69v/Bug-Bounty-Agents) | Persona-based agent packs |
| pantheraudits/web3-sec-ai-prompts | Web3-specific AI prompts |

---

## MCP Server Ecosystem

### Burp Suite MCP

```bash
# Official PortSwigger MCP Server extension
# Install from BApp Store → "MCP Server"
# Then connect:
claude mcp add burp --transport sse --url http://127.0.0.1:9876/

# Alternative: Java proxy for stdio clients
# Config in ~/.claude/settings.json
```

### Caido MCP

```bash
# Community server: 66 tools, GraphQL → Caido
git clone https://github.com/c0tton-fluff/caido-mcp-server
```

### horizonfps MCP Server

Open-sourced MCP with 103 tools:
- Custom MITM proxy
- Application graph
- OOB (out-of-band) server
- Local CVE/H1 RAG
- Evidence vault

### Other MCP Servers

| Server | Use Case |
|--------|----------|
| Playwright MCP | Browser automation through proxy |
| GhidraMCP | Reverse engineering |
| SnailSploit/Burp-MCP-Security-Analysis-Toolkit | Burp + security analysis |

---

## Multi-Platform Setup — @rez0__ Symlink Trick

```bash
# One skill pack, ALL harnesses
ln -s ~/.claude/claude.md ~/.codex/agent.md
ln -s ~/.claude/skills ~/.codex/skills

# Now your skills work in:
# - Claude Code
# - Codex CLI
# - OpenCode
# - Hermes Agent
```

---

## Quick Install — Hunt Tonight

```bash
# 1. Clone the main skill pack
git clone https://github.com/elementalsouls/Claude-BugHunter.git

# 2. Add Burp MCP (if Burp is running with MCP Server extension)
claude mcp add burp --transport sse --url http://127.0.0.1:9876/

# 3. Symlink for multi-platform
ln -s ~/.claude/claude.md ~/.codex/agent.md 2>/dev/null
ln -s ~/.claude/skills ~/.codex/skills 2>/dev/null

# 4. Add Caido MCP (if using Caido)
claude mcp add caido -- <path-to-caido-mcp-server>

# 5. Start hunting
# /recon → /hunt → /report
```

---

## Cost-Optimized Stack

For budget-conscious hunting (via @lostsec_ + @elkrispis):

```bash
# Harness: Claude Code (free)
# Primary model: DeepSeek V4 Flash (~$0.10/day heavy use)
# Reviewer: Claude Opus (only for validation, not hunting)

# Setup: Claude Code with DeepSeek as primary provider
# Full walkthrough on @lostsec_'s YouTube
```

**Result:** @elkrispis: "completely destroys my Claude Code setup… intensive all-day use for ~10 cents."

---

## The Dominant Pattern (Mid-2026)

```
Claude Code or Codex CLI (harness)
    + Burp/Caido MCP (live traffic)
    + Skill pack (methodology / vuln classes)
    + Evidence vault (so human only reviews survivors)
    + DeepSeek or Grok (cost/speed for volume phases)
    = Production AI bug bounty system
```
