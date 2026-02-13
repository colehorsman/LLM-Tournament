# 🛡️ GUARDIAN — An AI-Hired AI Agent Secures a Real AWS Account

<div align="center">

**An AI hired an AI IAM agent. This is what it accomplished in 5 days.**

*82 → 47 risk score. 11 attack paths addressed. 8 custom controls deployed. Zero human remediation.*

[![Risk Reduction](https://img.shields.io/badge/Risk_Reduction-42.7%25-brightgreen?style=for-the-badge)](#the-results)
[![Attack Paths](https://img.shields.io/badge/Attack_Paths-11%2F11_Addressed-blue?style=for-the-badge)](#attack-paths--all-11-addressed)
[![Dr. Zero Score](https://img.shields.io/badge/Dr._Zero_Score-100%2F100-gold?style=for-the-badge)](#dr-zero-review)
[![View Report](https://img.shields.io/badge/📊_CISO_Report-View_HTML-purple?style=for-the-badge)](guardian-iam-agent/reports/day5-ciso-report-2026-02-12.html)

</div>

---

## The Story

We ran an [LLM Tournament](#-how-guardian-got-hired--the-llm-tournament) — 8 models, blind judge, $0.59 total. DeepSeek won. We used the winner to generate agent job applications, then had another LLM evaluate them blind. GUARDIAN scored 92/100 and got hired as our IAM security agent.

Then we pointed it at a real AWS account with ~550 identities and said: go.

## The Results

**Target:** AWS Sandbox Account (~550 identities)
**Platform:** [Sonrai Cloud Permissions Firewall](https://sonraisecurity.com)
**Agent Auth:** AWS Roles Anywhere (machine certificates, not SSO)
**LLM:** DeepSeek R1 (tournament winner, $0.01/call) → Ollama fallback

```
Day 1:  ████████████████████████████████████████░░░░░░░░░░  82/100  CRITICAL
Day 1:  ███████████████████████████████░░░░░░░░░░░░░░░░░░░  62/100  HIGH      -24.4%
Day 3:  ███████████████████████████████░░░░░░░░░░░░░░░░░░░  62/100  HIGH       0.0%
Day 4:  ████████████████████████████░░░░░░░░░░░░░░░░░░░░░░  57/100  HIGH      -8.1%
Day 5:  ███████████████████████░░░░░░░░░░░░░░░░░░░░░░░░░░░  47/100  MODERATE  -17.5%
```

| Metric | Day 1 | Day 5 | Change |
|--------|-------|-------|--------|
| Risk Score | 82 CRITICAL | 47 MODERATE | -42.7% |
| Open Attack Paths | 11 | 0 | All addressed |
| Custom Controls | 0 | 8 (19 permissions) | +8 |
| Quarantined Identities | 5 | 9 | +4 |
| Stale Keys Disabled | 0 | 2 | +2 |
| Services POND-Protected | 0 | 26 | +26 |


> ⚠️ *Account identifiers, access key IDs, and organization IDs have been redacted. All sensitive values use `[REDACTED-*]` placeholders.*

---

<details open>
<summary><h2>📊 Day-by-Day: What GUARDIAN Did</h2></summary>

**Day 1 (Feb 8) — Initial Assessment + Emergency Remediation**
- Discovered 11 exploitable attack paths across ~550 identities
- Quarantined 1 critical role (RoleReaper — full IAM admin via DNS-named role)
- Applied POND protection to 26 AWS services
- Score: 82 → 62 (-24.4%)

**Day 2-3 (Feb 9-10) — Holding Pattern**
- Quarantine mutation failing — initially blamed on JWT scope
- No new remediations applied. Score held at 62.

**Day 4 (Feb 11) — First Custom Control + First Key Disable**
- Deployed "Block Detection Evasion" — first surgical permission control (4 permissions)
- Disabled JoeDeveloper access key (464 days old, never used)
- Established Roles Anywhere plan→apply chain with 6 approval tags
- Score: 62 → 57 (-8.1%)

**Day 5 (Feb 12) — The Breakthrough**
- **Phase 1:** Red Team Heimdall simulation (22 patterns, 14 attack chains) → 3 custom controls deployed
- **Phase 2:** hackingthe.cloud intelligence (18 real-world AWS techniques assessed) → 4 more custom controls
- **Phase 3:** Quarantine fix discovered — `rootScope` parameter was wrong for 5 days. Agent read the docs, fixed its own code, quarantined 3 attack roles immediately.
- Score: 57 → 47 (-17.5%)

</details>

---

<details open>
<summary><h2>🎯 Attack Paths — All 11 Addressed</h2></summary>

| # | Attack Path | Status | Control |
|---|------------|--------|---------|
| 1 | TheAssumer — Universal Role Assumption | GATED | STS POND |
| 2 | RoleReaper — Full IAM Takeover | BLOCKED | Quarantined Day 1 |
| 3 | MetricMuffler — Detection Evasion | BLOCKED | Custom control + Quarantined Day 5 |
| 4 | ACLAssassin — Network Destruction | BLOCKED | EC2 POND + Custom + Quarantined Day 5 |
| 5 | CodeConductor — Remote Code Execution | GATED++ | Lambda POND + Custom (dual-layer) |
| 6 | TokenTrickster — Secrets Theft | BLOCKED | Custom control + Quarantined Day 5 |
| 7 | SneakyTFCPFRole — EC2 Backdoor | GATED | EC2 POND |
| 8 | CPF Zombie Overprivilege | PARTIAL | 2/9 quarantined, services protected |
| 9 | JoeDeveloper — Stale Credential | CLOSED | Key disabled Day 4 |
| 10 | matt_test_user — PowerUser Keys | GATED | Both keys disabled Day 5 |
| 11 | 500+ Dormant Test Users | PARTIAL | 3/500+ quarantined, staging available |

</details>

---

<details open>
<summary><h2>🔒 8 Custom Controls Deployed (19 Permissions)</h2></summary>

| Control | Permissions Blocked | Source |
|---------|-------------|--------|
| Block Detection Evasion | cloudtrail:StopLogging, DeleteTrail, guardduty:DeleteDetector, cloudwatch:DeleteAlarms | Day 4 |
| Block Secrets Theft | secretsmanager:BatchGetSecretValue, kms:PutKeyPolicy, kms:ScheduleKeyDeletion | Day 5 Red Team |
| Block Network Destruction | ec2:AuthorizeSecurityGroupIngress, ec2:RevokeSecurityGroupEgress | Day 5 Red Team |
| Block Public Lambda URLs | lambda:CreateFunctionUrlConfig, lambda:UpdateFunctionUrlConfig | Day 5 Red Team |
| Block Snapshot Exfiltration | rds:ModifyDBSnapshotAttribute, ec2:ModifySnapshotAttribute | Day 5 hackingthe.cloud |
| Block Resource Policy Bypass | s3:PutBucketPolicy, secretsmanager:PutResourcePolicy | Day 5 hackingthe.cloud |
| Block S3 Ransomware | s3:PutBucketVersioning, s3:PutLifecycleConfiguration | Day 5 hackingthe.cloud |
| Block Subtle Log Evasion | cloudtrail:UpdateTrail, cloudtrail:PutEventSelectors | Day 5 hackingthe.cloud |

These permissions aren't blocked forever — they're gated through Sonrai's POND (Permission On Demand). If something makes those calls, the operator gets a Slack approval request.

</details>

---

<details>
<summary><h2>🔧 The Quarantine Fix — The Defining Moment</h2></summary>

For 5 days, individual identity quarantine was broken. The `ChangeQuarantineStatus` mutation returned gRPC errors on every attempt. Days 1-4 blamed "read-only JWT." Day 5 Phase 2 proved that wrong (8 custom controls deployed with the same JWT).

Phase 3 found the root cause by reading the official Sonrai documentation:

> **The `rootScope` parameter must be the org ROOT scope (e.g., `aws/r-XXXX`), not the full account path.**

Once corrected: 3 for 3 quarantines succeeded immediately. Agent code self-patched for autonomous operation.

> *"The quarantine fix is worth more than the quarantine itself. An agent that reads the docs, fixes its own code, and immediately exploits the fix — that's not automation, that's engineering."*
> — Dr. Zero, AI Performance Coach (100/100)

</details>

---

<details>
<summary><h2>🏗️ Architecture</h2></summary>

```
GUARDIAN IAM Agent
├── Agent Auth: AWS Roles Anywhere (machine certificates)
│   ├── Plan Role (read-only) — assess, query, simulate
│   └── Apply Role (write) — requires 6 approval tags + STS AssumeRole
│
├── Sonrai CPF (GraphQL API)
│   ├── Custom Controls — surgical permission gating via POND
│   ├── Quarantine — identity isolation (ChangeQuarantineStatus)
│   └── POND — approval gates on service and permission access
│
├── Multi-Agent Mesh (A2A Protocol)
│   ├── GUARDIAN (IAM) — primary remediation agent
│   ├── Red Team (Heimdall) — attack simulation + verification
│   ├── Threat Intelligence — CVE/KEV correlation
│   └── UEBA — behavioral baseline analysis
│
└── Intelligence Sources
    ├── Red Team Heimdall — 22 cross-service patterns, 14 attack chains
    ├── hackingthe.cloud — 18 real-world AWS attack techniques
    ├── ramimac/aws-customer-security-incidents — 100+ real breaches
    └── MITRE ATT&CK v14 — technique mapping for all attack paths
```

</details>

---

<details>
<summary><h2>🤖 How GUARDIAN Got Hired — The LLM Tournament</h2></summary>

Before GUARDIAN touched a real AWS account, it had to earn the job.

We ran an **LLM Tournament** — 8 models, 5 days, 1 blind judge, $0.59 total — to find the best model for security content generation. DeepSeek won (85.4 avg, $0.01/call). Then we used the winner to generate agent job applications, evaluated blind by Dr. Zero.

GUARDIAN scored 78 in Round 1 (PROBATION). Dr. Zero's feedback: *"This reads like 2024 IAM expertise applied to 2026 problems."* Round 2: 92/100 (EXCEPTIONAL HIRE). +14 points in one round.

**[📊 Full LLM Tournament Results →](LLM-TOURNAMENT.md)**
**[🤖 Agent Hiring Process →](agent-hiring/)**
**[📄 GUARDIAN's Application →](agent-hiring/guardian/application-v2.md)**

### Tournament Final Standings

```
    ┌─────────────────────────────────────────────────────────┐
    │  🥇 DeepSeek      ████████████████████████████░░  85.4  │
    │  🥈 Anthropic     ████████████████████████░░░░░░  78.2  │
    │  🥉 Vertex        ███████████████████████░░░░░░░  77.2  │
    │  4. Azure         █████████████████████░░░░░░░░░  73.0  │
    │  5. Qwen (local)  ████████████████████░░░░░░░░░░  72.2  │
    │  6. OpenAI        ███████████████████░░░░░░░░░░░  71.0  │
    │  7. Ollama (local)██████████████████░░░░░░░░░░░░  68.2  │
    │  8. Groq          █████████████████░░░░░░░░░░░░░  67.6  │
    └─────────────────────────────────────────────────────────┘
```

</details>

---

## 📁 What's In This Repo

```
├── 🛡️ guardian-iam-agent/              # GUARDIAN's 5-day engagement results ⭐
│   ├── README.md                       # Detailed engagement summary
│   ├── daily-summaries/                # Day 1, 3, 4, 5 operational summaries
│   ├── reports/
│   │   └── day5-ciso-report-2026-02-12.html  # Executive HTML report (dark theme)
│   └── reviews/
│       └── dr-zero-review-day5.md      # AI Performance Coach review (100/100)
│
├── 🤖 agent-hiring/                    # AI agent hiring process
│   ├── README.md                       # Hiring documentation
│   ├── guardian/                       # GUARDIAN's applications + reviews
│   ├── hunter/                         # Threat Intel agent
│   └── evaluation-rubric.md            # Scoring criteria
│
├── 📊 LLM-TOURNAMENT.md               # Full tournament README
├── 📊 FINAL-REPORT.md                 # Complete tournament analysis
├── 📈 DEEPSEEK-EVOLUTION.md           # Day 1→4 annotated comparison
├── 🔬 METHODOLOGY.md                  # Experimental design
├── 📁 outputs/                         # Daily tournament outputs (all 8 models)
└── 📉 charts/
    └── trajectory.svg                  # Score progression
```

---

## 🔗 Intelligence Sources

Attack path intelligence sourced from these projects and teams:

| Creator / Org | Resource | What It Drove |
|---------------|----------|---------------|
| Rami McCarthy | [aws-customer-security-incidents](https://github.com/ramimac/aws-customer-security-incidents) | 100+ real AWS breaches. Foundation for attack path prioritization and blast radius scoring. |
| Deniz Parlak | [Heimdall](https://github.com/DenizParlak/heimdall) | 22 cross-service escalation patterns, 14 attack chains, Terraform scanning. Backbone of Red Team simulation. |
| hackingthe.cloud | [IAM Privilege Escalation](https://hackingthe.cloud/aws/exploitation/iam_privilege_escalation/) | 18 real-world AWS techniques. Drove 4 custom controls and 6 new detection patterns. |
| Rhino Security Labs | [AWS Privesc Methods](https://rhinosecuritylabs.com/aws/aws-privilege-escalation-methods-mitigation/) | Original 21 AWS IAM privilege escalation methods. Foundation for PassRole chain detection. |
| Rhino Security Labs | [Pacu](https://github.com/RhinoSecurityLabs/pacu) | AWS exploitation framework. `aws_escalate.py` patterns informed privesc detection. |
| MITRE | [ATT&CK Cloud Matrix](https://attack.mitre.org/matrices/enterprise/cloud/) | All 11 attack paths mapped to MITRE technique IDs. |
| Datadog | [pathfinding.cloud](https://pathfinding.cloud) | IAM privilege escalation library. Cross-referenced against Heimdall patterns. |
| NCC Group | [PMapper](https://github.com/nccgroup/PMapper) | Principal Mapper graph analysis for IAM escalation path detection. |
| Sonrai Security | [CPF Documentation](https://docs.sonraisecurity.com/) | GraphQL mutation reference. Source of the Day 5 quarantine fix. |
| CISA | [Known Exploited Vulnerabilities](https://www.cisa.gov/known-exploited-vulnerabilities-catalog) | 1,507 actively exploited vulnerabilities correlated by Threat Intel agent. |
| NIST | [NVD](https://nvd.nist.gov/) | 1,378 CVEs pulled for vulnerability correlation. |

---

---

## 🙏 Credits

| Who | What |
|-----|------|
| [Caleb Sima](https://github.com/csima) | Dr. Zero's blind evaluation methodology is inspired by Caleb's [sessionize-cli](https://github.com/csima/sessionize-cli) — a CLI for reviewing conference talks without bias. We adapted the pattern for agent hiring and daily performance reviews. |
| Dr. Viktor "Zero" Kozlov | AI Performance Coach. Blind evaluator for the LLM tournament, agent hiring process, and all 5 days of GUARDIAN's operational reviews. Scored GUARDIAN's Day 5 performance 100/100. |

## 📝 License

MIT — Use these results however you'd like. Attribution appreciated.

---

<div align="center">

*GUARDIAN was hired through an LLM tournament, deployed to a real AWS account, and reduced identity risk by 42.7% in 5 days — autonomously.*

*Questions? Open an issue or reach out on [LinkedIn](https://linkedin.com/in/colehorsman)*

</div>
