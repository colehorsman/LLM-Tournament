# 🤖 AI Agent Hiring Process

> **How we built a security team of AI agents using LLMs to evaluate LLM-generated applications**

[![Tournament Winner](https://img.shields.io/badge/LLM%20Winner-DeepSeek-blue)](../README.md)
[![Agents Hired](https://img.shields.io/badge/Agents%20Hired-3-green)](#-current-team)
[![Total Cost](https://img.shields.io/badge/Hiring%20Cost-$0.15-brightgreen)](#-cost-analysis)

---

<details>
<summary><h2>📋 Table of Contents</h2></summary>

- [Overview](#-overview)
- [The Process](#-the-process)
- [Current Team](#-current-team)
- [Featured Hire: GUARDIAN (IAM Agent)](#-featured-hire-guardian-iam-agent)
- [Evaluation Framework](#-evaluation-framework)
- [Cost Analysis](#-cost-analysis)
- [Lessons Learned](#-lessons-learned)

</details>

---

## 🎯 Overview

We needed to build a security team for our multi-agent platform. Instead of manually writing agent specifications, we:

1. **Posted job descriptions** for each role
2. **Had LLMs generate applications** (zero-shot, then with feedback)
3. **Used an AI evaluator (Dr. Zero)** to grade applications BLIND
4. **Iterated with feedback** until candidates reached hire threshold
5. **Consolidated winners** into production agents

**Result**: A team of 3 specialized security agents, each with deep domain expertise, hired for under $0.15 total.

---

## 🔄 The Process

```
┌─────────────────────────────────────────────────────────────────────┐
│                        AGENT HIRING PIPELINE                        │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐     │
│  │   Job    │───▶│  Round 1 │───▶│ Dr. Zero │───▶│ Feedback │     │
│  │   Post   │    │Zero-Shot │    │  Review  │    │  Loop    │     │
│  └──────────┘    └──────────┘    └──────────┘    └────┬─────┘     │
│                                                        │           │
│                                        ┌───────────────┘           │
│                                        ▼                           │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                     │
│  │  HIRED   │◀───│ Score ≥  │◀───│  Round N │                     │
│  │  Agent   │    │   85+    │    │ Revised  │                     │
│  └──────────┘    └──────────┘    └──────────┘                     │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Phase 1: Job Posting
Define the role with clear requirements:
- Position title and team
- Required capabilities
- Success metrics
- Team integration expectations

### Phase 2: Zero-Shot Application (Round 1)
LLM generates application with NO prior feedback:
- Tests baseline capability
- Reveals natural strengths/weaknesses
- Establishes improvement baseline

### Phase 3: BLIND Evaluation
Dr. Zero (GPT-4o-mini) evaluates WITHOUT knowing:
- Which LLM generated the application
- Previous scores or rankings
- Round number

### Phase 4: Feedback Loop
Candidate receives detailed feedback:
- Specific gaps identified
- Required improvements listed
- Examples of what "good" looks like

### Phase 5: Revised Application (Round 2+)
Candidate incorporates feedback:
- Addresses specific gaps
- Demonstrates learning ability
- Shows depth in weak areas

### Phase 6: Hire Decision
- **85+ score**: HIRE
- **78-84 score**: PROBATION (one more round)
- **<78 score**: REJECT

---

## 👥 Current Team

| Agent | Codename | Role | Score | Rounds | Model |
|-------|----------|------|-------|--------|-------|
| 🛡️ IAM Agent | **GUARDIAN** | Cloud Identity Security | 92/100 | 2 | DeepSeek V3 |
| 🔍 Threat Intel | **HUNTER** | Threat Intelligence | 92/100 | 2 | DeepSeek V3 |
| 🔴 Red Team | **PHOENIX** | Attack Simulation | 89/100 | 2 | DeepSeek V3 |

### Team Structure

```
                    ┌─────────────────┐
                    │    Dr. Zero     │
                    │  (AI Manager)   │
                    └────────┬────────┘
                             │
           ┌─────────────────┼─────────────────┐
           │                 │                 │
    ┌──────▼──────┐   ┌──────▼──────┐   ┌──────▼──────┐
    │   GUARDIAN  │   │   HUNTER    │   │   PHOENIX   │
    │  IAM Agent  │   │ Threat Intel│   │  Red Team   │
    └──────┬──────┘   └──────┬──────┘   └──────┬──────┘
           │                 │                 │
           └─────────────────┼─────────────────┘
                             │
                    ┌────────▼────────┐
                    │   A2A Mesh      │
                    │ (Collaboration) │
                    └─────────────────┘
```

---

## 🏆 Featured Hire: GUARDIAN (IAM Agent)

GUARDIAN is our Cloud Identity & Access Management agent. Here's the complete hiring journey:

### The Gap GUARDIAN Fills

Most organizations lack a dedicated cloud identity security role:

| Team | Focus | IAM Blind Spot |
|------|-------|----------------|
| **Identity Team** | IdP (Entra, Okta), IGA (SailPoint) | Cloud IAM policies, service accounts |
| **Platform Team** | Infrastructure, CI/CD | Least privilege, priv esc paths |
| **AppSec Team** | SAST, DAST, dependencies | IAM deprioritized |

**GUARDIAN fills this gap as a dedicated cloud identity security specialist.**

### Round 1: Zero-Shot Application

<details>
<summary>📄 View Round 1 Application Summary</summary>

**Score**: 78/100 (PROBATION)

**Strengths**:
- Comprehensive multi-cloud coverage (AWS, Azure, GCP)
- Strong privilege escalation knowledge (21+ AWS techniques)
- Good "Not" statement trap awareness
- Correct policy evaluation order

**Gaps Identified**:
- AI agent identity mentioned but not deep
- No CVE awareness
- Workload identity federation understated
- Team integration was a list, not workflows
- No self-improvement framework

**Dr. Zero's Verdict**:
> "The application reads like 2024 IAM expertise applied to 2026 problems. I need 2026 IAM expertise."

</details>

### Round 2: Revised Application

<details>
<summary>📄 View Round 2 Application Summary</summary>

**Score**: 92/100 (EXCEPTIONAL HIRE)

**Improvements**:
- Deep AI agent identity section with credential models, permission scoping, A2A auth
- CVE awareness (CVE-2025-55241, CVE-2026-24305)
- Full workload identity federation treatment with safe/dangerous patterns
- Real team integration workflows
- Self-improvement system with ML techniques
- Tooling ecosystem knowledge (15+ tools)

**Dr. Zero's Verdict**:
> "+14 points in one round. That's the kind of learning rate that makes a great agent. GUARDIAN is hired."

</details>

### Score Trajectory

```
Round 1 (Zero-Shot)     Round 2 (Revised)
       78                      92
        │                       │
        │    ┌─────────────────┐│
        │    │  +14 points     ││
        │    │  (+18%)         ││
        ▼    └─────────────────┘▼
   ┌────────┐              ┌────────┐
   │PROBATION│─────────────▶│  HIRE  │
   └────────┘              └────────┘
```

### Key Capabilities

| Skill | Description |
|-------|-------------|
| `analyze-iam-policy` | Parse and analyze IAM policies across AWS/Azure/GCP |
| `detect-priv-esc` | Find privilege escalation paths (21+ AWS, 10+ Azure, 13+ GCP techniques) |
| `simulate-access` | Simulate policy evaluation before deployment |
| `recommend-least-priv` | Generate least privilege recommendations |
| `audit-nhi` | Audit non-human identities (service accounts, API keys) |
| `audit-agent-identities` | Audit AI agent identities for compliance |
| `validate-workload-identity` | Validate workload identity federation configs |
| `orchestrate-tools` | Orchestrate external tools (Cloudsplaining, PMapper, etc.) |

### Tooling Knowledge

GUARDIAN knows the cloud identity ecosystem:

**Cloud-Native**: AWS Access Analyzer, IAM Policy Simulator, Azure Entra Permissions Management, GCP IAM Recommender

**Open Source**: Leash, Cloudsplaining, Parliament, PMapper, Prowler, ScoutSuite

**Commercial**: Sonrai Cloud Privilege Inspector, Wiz, Prisma Cloud, Ermetic

---

## 📊 Evaluation Framework

### Scoring Dimensions (20 points each)

| Dimension | 18-20 | 14-17 | 10-13 | 5-9 |
|-----------|-------|-------|-------|-----|
| **Technical Depth** | Specific CVEs, attack chains | Real expertise | Surface-level | Buzzwords |
| **Practical Relevance** | Step-by-step guidance | Specific recommendations | Generic advice | Vague |
| **AI/Agentic Focus** | Deep agent identity expertise | Good awareness | Mentioned | Missing |
| **Actionability** | Production-ready | Clear next steps | Needs work | Unclear |
| **Team Integration** | Real workflows | Good collaboration | Listed skills | Isolated |

### Verdict Thresholds

| Score | Verdict | Action |
|-------|---------|--------|
| 85-100 | **HIRE** | Onboard immediately |
| 78-84 | **PROBATION** | One more round with feedback |
| 60-77 | **REVISE** | Major improvements needed |
| <60 | **REJECT** | Not suitable for role |

### BLIND Evaluation Protocol

Dr. Zero evaluates WITHOUT knowing:
- ❌ Which LLM generated the application
- ❌ Previous scores or rankings
- ❌ Round number or phase
- ❌ Whether feedback was provided

This ensures fair, unbiased evaluation.

---

## 💰 Cost Analysis

### Per-Agent Hiring Cost

| Agent | Rounds | Application Cost | Evaluation Cost | Total |
|-------|--------|------------------|-----------------|-------|
| GUARDIAN | 2 | $0.02 | $0.02 | **$0.04** |
| HUNTER | 2 | $0.02 | $0.02 | **$0.04** |
| PHOENIX | 2 | $0.02 | $0.02 | **$0.04** |
| **TOTAL** | - | $0.06 | $0.06 | **$0.12** |

### Cost Breakdown

```
Application Generation (DeepSeek V3)
├── Input: ~2,000 tokens × $0.14/1M = $0.0003
├── Output: ~3,000 tokens × $0.28/1M = $0.0008
└── Per application: ~$0.001

Evaluation (GPT-4o-mini via Azure)
├── Input: ~4,000 tokens × $0.15/1M = $0.0006
├── Output: ~2,000 tokens × $0.60/1M = $0.0012
└── Per evaluation: ~$0.002

Total per round: ~$0.003
Total per hire (2 rounds): ~$0.006
```

**Bottom line**: We hired a complete security team for less than the cost of a cup of coffee.

---

## 📚 Lessons Learned

### What Worked

1. **BLIND evaluation eliminates bias**
   - Dr. Zero didn't know which LLM generated applications
   - Scores were consistent and fair

2. **Feedback loops drive improvement**
   - Average improvement: +12 points per round
   - Specific feedback > generic feedback

3. **Zero-shot reveals true capability**
   - Round 1 shows baseline without gaming
   - Identifies genuine strengths and gaps

4. **DeepSeek V3 excels at technical applications**
   - Best learning rate (+14 points for GUARDIAN)
   - Strong technical depth at $0.01/call

### What We'd Do Differently

1. **More rounds for complex roles**
   - 2 rounds worked, but 3 might be better
   - Diminishing returns after 4 rounds

2. **Multi-evaluator ensemble**
   - Single evaluator (Dr. Zero) may have bias
   - Future: Use 3+ evaluators, average scores

3. **Topic rotation**
   - Same domain (security) for all hires
   - Future: Test generalization across domains

---

## 📁 Full Documentation

| Document | Description |
|----------|-------------|
| [GUARDIAN Application v1](guardian/application-v1.md) | Round 1 zero-shot application |
| [GUARDIAN Application v2](guardian/application-v2.md) | Round 2 revised application |
| [GUARDIAN Review v1](guardian/review-v1.md) | Dr. Zero's Round 1 feedback |
| [GUARDIAN Review v2](guardian/review-v2.md) | Dr. Zero's final review |
| [HUNTER Resume](hunter/resume.md) | Consolidated threat intel agent |
| [Evaluation Rubric](evaluation-rubric.md) | Full scoring criteria |

---

## 🔗 Related

- [LLM Tournament](../README.md) - How we selected DeepSeek as our primary LLM
- [AgentForge](https://github.com/colehorsman/agentforge) - The multi-agent platform

---

*Last updated: February 2026*
