# Skills & Commands Reference

## How to Invoke

| Method | Syntax | Example |
|--------|--------|---------|
| Slash command | `/command-name` | `/recon`, `/hunt`, `/triage` |
| Auto-trigger | Describe the bug class in natural language | "I found reflected input on a login form, testing for XSS" → triggers `hunt-xss` |
| Explicit invoke | `/skill-name` | `/ai-hunting` |

---

## ⚡ AI Bug Bounty (Your Custom Skill)

| Skill | What It Does |
|-------|-------------|
| `/ai-hunting` | Full AI-assisted hunting — prompts (wp2shell, focused weirdness, keep-going loop), model routing, harness design, system building. Invoke this for ANY AI + bug bounty task. |

---

## Orchestration (Start Here)

| Command | What It Does |
|---------|-------------|
| `/hunt` | Start a hunt session |
| `/recon` | Run recon on target |
| `/surface` | Map attack surface |
| `/chain` | Chain bugs together (A→B escalation) |
| `/autopilot` | Autonomous hunting mode |
| `/pickup` | Resume from where you left off |
| `/intel` | Gather intelligence on target |
| `/scope` | Check program scope |
| `/remember` | Save findings to memory |
| `/memory-gc` | Clean up memory store |
| `/token-scan` | Scan for exposed tokens/secrets |
| `/web3-audit` | Web3/smart contract audit mode |

---

## Validation & Reporting

| Command | What It Does |
|---------|-------------|
| `/triage` | Run 7-Question Gate on a finding |
| `/validate` | Validate a finding before submitting |
| `/report` | Generate a report |

---

## Vulnerability Classes — Hunt Skills

Trigger these by describing the bug you're testing:

### Tier 1 — Always Critical

| Skill | Triggers When |
|-------|--------------|
| `hunt-rce` | Testing for command injection, code execution |
| `hunt-ato` | Testing for account takeover |
| `hunt-auth-bypass` | Testing authentication bypass |
| `hunt-sqli` | Testing SQL injection |
| `hunt-ssrf` | Testing SSRF |
| `hunt-deserialization` | Testing insecure deserialization |
| `hunt-ssti` | Testing server-side template injection |
| `hunt-xxe` | Testing XML external entity injection |

### Tier 2 — High Value

| Skill | Triggers When |
|-------|--------------|
| `hunt-idor` | Testing IDOR / broken access control |
| `hunt-business-logic` | Testing business logic flaws |
| `hunt-race-condition` | Testing race conditions |
| `hunt-jwt-crypto` | Testing JWT attacks (alg:none, key confusion) |
| `hunt-oauth` | Testing OAuth/OIDC flows |
| `hunt-graphql` | Testing GraphQL endpoints |
| `hunt-file-upload` | Testing file upload bypass |
| `hunt-saml` | Testing SAML/SSO |
| `hunt-http-smuggling` | Testing HTTP request smuggling |
| `hunt-cache-poison` | Testing web cache poisoning |
| `hunt-lfi` | Testing local file inclusion |

### Tier 3 — Common

| Skill | Triggers When |
|-------|--------------|
| `hunt-xss` | Testing XSS (reflected, stored, DOM) |
| `hunt-csrf` | Testing CSRF |
| `hunt-host-header` | Testing host header injection |
| `hunt-open-redirect` | Testing open redirect |
| `hunt-nosqli` | Testing NoSQL injection |
| `hunt-ldap` | Testing LDAP injection |
| `hunt-html-injection` | Testing HTML injection |
| `hunt-clickjacking` | Testing clickjacking |
| `hunt-cors` | Testing CORS misconfig |
| `hunt-dom` | Testing DOM-based vulnerabilities |

### Auth & Session

| Skill | Triggers When |
|-------|--------------|
| `hunt-mfa-bypass` | Testing MFA/2FA bypass |
| `hunt-forgot-password` | Testing password reset flow |
| `hunt-session` | Testing session management |
| `hunt-brute-force` | Testing brute force / rate limiting |
| `hunt-captcha-bypass` | Testing CAPTCHA bypass |

### API & Architecture

| Skill | Triggers When |
|-------|--------------|
| `hunt-api-misconfig` | Testing API misconfig (mass assignment, prototype pollution) |
| `hunt-spa-api` | Testing SPA API endpoints |
| `hunt-websocket` | Testing WebSocket endpoints |
| `hunt-grpc` | Testing gRPC services |
| `hunt-rag-vector` | Testing RAG/vector DB attacks |
| `hunt-shadow-api` | Testing undocumented/shadow APIs |
| `hunt-dispatch` | Testing request dispatch issues |

### Cloud & Infrastructure

| Skill | Triggers When |
|-------|--------------|
| `hunt-k8s` | Testing Kubernetes |
| `hunt-cloud-misconfig` | Testing cloud misconfig (AWS, GCP, Azure) |
| `hunt-tls-network` | Testing TLS/network issues |
| `hunt-subdomain` | Testing subdomain takeover |
| `hunt-source-leak` | Testing source code leaks |
| `hunt-cicd` | Testing CI/CD pipeline |
| `hunt-ntlm-info` | Testing NTLM info disclosure |

### Framework-Specific

| Skill | Triggers When |
|-------|--------------|
| `hunt-laravel` | Testing Laravel apps |
| `hunt-nextjs` | Testing Next.js apps |
| `hunt-nodejs` | Testing Node.js apps |
| `hunt-springboot` | Testing Spring Boot apps |
| `hunt-aspnet` | Testing ASP.NET apps |
| `hunt-sharepoint` | Testing SharePoint |

### AI / LLM Testing

| Skill | Triggers When |
|-------|--------------|
| `hunt-llm-ai` | Testing AI/LLM features (prompt injection, etc.) |
| `hunt-llm-injection` | Testing LLM prompt injection specifically |

### Specialty

| Skill | Triggers When |
|-------|--------------|
| `hunt-misc` | Testing miscellaneous/unique vulns |
| `hunt-exceptional-conditions` | Testing edge cases, unexpected input |

---

## Methodology & Process Skills

| Skill | What It Does |
|-------|-------------|
| `bb-methodology` | Full 5-phase non-linear hunting workflow — invoke at session start or when stuck |
| `bug-bounty` | Complete bug bounty orchestrator (recon → hunt → report) |
| `bb-local-toolkit` | Same as bug-bounty, but knows your local tools/wordlists/clones |
| `redteam-mindset` | Critical thinking framework for hunting |
| `recon-scope-triage` | Recon scope triage |
| `triage-validation` | Finding validation and triage |
| `evidence-hygiene` | Evidence collection best practices |
| `report-writing` | Report writing templates and guidance |
| `bugcrowd-reporting` | Bugcrowd-specific reporting format |

## Recon Skills

| Skill | What It Does |
|-------|-------------|
| `web2-recon` | Web/API recon |
| `js-analyzer` | JavaScript bundle analysis |
| `offensive-osint` | OSINT for bug bounty |
| `osint-methodology` | OSINT methodology framework |
| `recon-bb` | Bug bounty recon |
| `session-search` | Session token search |

## Specialty Skills

| Skill | What It Does |
|-------|-------------|
| `security-arsenal` | Tool selection for any vuln class |
| `hunt-dispatch` | Route to correct hunt skill based on bug class |
| `supply-chain-attack-recon` | Supply chain attack surface |
| `mid-engagement-ir-detection` | Detect if target is responding to your testing |
| `validator` | Validate findings before reporting |

## Red Team / Enterprise

| Skill | What It Does |
|-------|-------------|
| `apk-redteam-pipeline` | Android APK red-team pipeline |
| `ios-redteam-pipeline` | iOS red-team pipeline |
| `cloud-iam-deep` | Cloud IAM deep dive |
| `enterprise-vpn-attack` | Enterprise VPN attack surface |
| `m365-entra-attack` | Microsoft 365 / Entra ID attack |
| `okta-attack` | Okta attack surface |
| `vmware-vcenter-attack` | VMware vCenter attack |
| `meme-coin-audit` | Meme coin / crypto audit |
| `web3-audit` | Web3 smart contract audit |

---

## 🎯 Quick Start — Tonight's Hunt

```bash
# 1. Scaffold your target
hunt my-target-name

# 2. Edit scope.md with program details
# 3. Start Claude Code
claude

# 4. Inside Claude Code:
/recon              # Map the target
/hunt               # Start hunting
/triage             # Validate any findings
/report             # Generate report
```

## 🎯 AI-Assisted Hunting (Your Research)

```bash
/ai-hunting         # Load the full AI bug bounty research context
                    # Use for: prompt crafting, model routing, system design,
                    # wp2shell methodology, focused weirdness, adversarial validation
```
