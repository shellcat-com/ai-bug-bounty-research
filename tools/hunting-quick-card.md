# Bug Bounty Hunting — Quick Reference Card

Print this. Keep it open. This is your hunting console.

---

## Session Flow

```
1. claude                          # Open Claude Code (or codex for long autonomous runs)
2. /memory-inject                  # Load past findings, gadgets, patterns
3. /recon                          # Map the target
4. Talk normally                   # "Testing for XSS on the search endpoint..."
5. /adversarial-validate           # Validate anything you find
6. /report                         # Generate submission-ready report
```

---

## Skills You Actually Call

| When | Type |
|------|------|
| **Session start** | `/memory-inject` |
| **Map target** | `/recon` |
| **Need AI research help** | `/ai-hunting` |
| **Found a bug → validate** | `/adversarial-validate` |
| **Generate report** | `/report` |
| **Validate existing finding** | `/triage` |
| **Chain bugs together** | `/chain` |
| **Autonomous mode** | `/autopilot` |
| **Build micro-agents** | `/hackbot-patterns` |

---

## Hunt Skills — Just Describe the Bug

These trigger automatically. Don't call them. Just describe what you're testing.

| You say... | Triggers |
|------------|----------|
| "Testing IDOR on /api/users/123" | `hunt-idor` |
| "Reflected input, testing XSS" | `hunt-xss` |
| "SQL injection on search param" | `hunt-sqli` |
| "SSRF in webhook URL" | `hunt-ssrf` |
| "Auth bypass on admin endpoint" | `hunt-auth-bypass` |
| "JWT token — testing alg:none" | `hunt-jwt-crypto` |
| "GraphQL introspection enabled" | `hunt-graphql` |
| "File upload — testing bypass" | `hunt-file-upload` |
| "Race condition on checkout" | `hunt-race-condition` |
| "OAuth redirect_uri parameter" | `hunt-oauth` |
| "SSTI in template parameter" | `hunt-ssti` |
| "Deserialization — Java app" | `hunt-deserialization` |
| "Cache poisoning — X-Forwarded-Host" | `hunt-cache-poison` |
| "HTTP request smuggling" | `hunt-http-smuggling` |
| "Password reset token leakage" | `hunt-forgot-password` |
| "MFA bypass attempt" | `hunt-mfa-bypass` |
| "WebSocket — testing auth" | `hunt-websocket` |
| "Mass assignment on profile update" | `hunt-api-misconfig` |
| "Prototype pollution in JSON merge" | `hunt-api-misconfig` |
| "Kubernetes — testing pod access" | `hunt-k8s` |
| "Cloud misconfig — S3 bucket" | `hunt-cloud-misconfig` |
| "Laravel debug mode exposed" | `hunt-laravel` |
| "Next.js SSR — testing cache" | `hunt-nextjs` |
| "Subdomain takeover" | `hunt-subdomain` |
| "CSRF on state-changing endpoint" | `hunt-csrf` |
| "Open redirect in login flow" | `hunt-open-redirect` |
| "Host header injection" | `hunt-host-header` |
| "XXE in XML upload" | `hunt-xxe` |
| "LFI in file parameter" | `hunt-lfi` |
| "Clickjacking on sensitive page" | `hunt-clickjacking` |
| "CORS misconfiguration" | `hunt-cors` |
| "Session fixation" | `hunt-session` |
| "gRPC — testing auth" | `hunt-grpc` |
| "NoSQL injection — MongoDB" | `hunt-nosqli` |
| "CI/CD pipeline exposure" | `hunt-cicd` |
| "Source code leak — .git exposed" | `hunt-source-leak` |
| "LLM prompt injection" | `hunt-llm-injection` or `hunt-llm-ai` |
| "NTLM info disclosure" | `hunt-ntlm-info` |
| "SAML authentication bypass" | `hunt-saml` |
| "Business logic — payment bypass" | `hunt-business-logic` |
| "Brute force — no rate limit" | `hunt-brute-force` |

---

## Model Routing (When to Use What)

| Phase | Model | Cost |
|-------|-------|------|
| Recon, volume scanning | DeepSeek V4 Flash | ~10¢/day |
| Deep hunting, code audit | Codex / GPT-5.6 Sol | $200/mo |
| Validation, review | Claude Opus | $20-200/mo |
| Speed recon, browser drive | Grok | X Premium |

---

## Validation Gate (Before Submitting ANYTHING)

```
/adversarial-validate

P8  → Validate + escalate (find the real impact ceiling)
P9  → Independently reproduce (prove it's not a fluke)
P10 → Hostile triage (try to KILL the finding)

Survives all 3? → /report → SUBMIT
Dies at any stage? → Fix and re-run, or discard
```

---

## Memory System

```
targets/
├── _shared/MEMORY.md          ← Cross-target gadgets, patterns, model log
├── <program>/
│   ├── notes/                 ← Observations, tech stack, recon
│   ├── leads/                 ← Unresolved leads
│   ├── gadgets/               ← Target-specific primitives
│   ├── findings/              ← Confirmed findings
│   └── reports/               ← Ready to submit
```

---

## Target Scaffold

```bash
hunt program-name          # Creates full engagement folder
ls ~/Targets/program-name/ # CLAUDE.md, scope.md, findings/, evidence/
```

---

## One-Liner Cheats

```bash
claude                     # Start Claude Code
codex                      # Start Codex CLI (long autonomous runs)
/memory-inject             # Load memory (ALWAYS do this first)
/recon                     # Map attack surface
/hunt                      # Start hunting
/adversarial-validate      # Gate a finding before submit
/report                    # Generate report
/ai-hunting                # Load AI research context
wc -l leads/*.md           # Count open leads
```

---

## The Golden Rules

1. **PC or GTFO** — Proof of concept or it doesn't exist
2. **Validate before submit** — P8 → P9 → P10. Every time.
3. **Write everything** — Leads, gadgets, findings to `targets/<program>/`
4. **Prompt is 5%, harness is 95%** — The system finds the bugs. The prompt just aims.
