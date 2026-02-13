# 🏆 LLM Tournament & AI Agent Hiring

<div align="center">

**8 LLMs. 5 Days. 1 Blind Judge. $0.59 Total.**

*Can a $0.01/call API beat a $3.00/call premium model at thought leadership?*

**Spoiler: Yes. By 7 points. Then we used it to hire AI agents.**

[![DeepSeek](https://img.shields.io/badge/Winner-DeepSeek-gold?style=for-the-badge)](outputs/day-04/deepseek.md)
[![Score](https://img.shields.io/badge/Peak_Score-93%2F100-brightgreen?style=for-the-badge)](outputs/day-04/deepseek.md)
[![Agents Hired](https://img.shields.io/badge/Agents_Hired-3-purple?style=for-the-badge)](#-agent-hiring-process)
[![Cost](https://img.shields.io/badge/Total_Cost-$0.59-blue?style=for-the-badge)](#cost-analysis)

</div>

---

<details open>
<summary><h2>🤖 Agent Hiring Process</h2></summary>

> **How we built a security team of AI agents using LLMs to evaluate LLM-generated applications**

After the tournament proved DeepSeek's quality, we used it to generate job applications for AI agent roles—then had another LLM (Dr. Zero) evaluate them BLIND.

### The Pipeline

```
┌──────────────────────────────────────────────────────────────────┐
│                     AGENT HIRING PIPELINE                        │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Job Post ──▶ Round 1 ──▶ Dr. Zero ──▶ Feedback ──▶ Round 2     │
│              (Zero-Shot)   (BLIND)      Loop        (Revised)    │
│                                                                  │
│                              │                         │         │
│                              ▼                         ▼         │
│                         Score < 85              Score ≥ 85       │
│                         PROBATION                  HIRE          │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Current Team

| Agent | Codename | Role | Score | Rounds | Cost |
|-------|----------|------|:-----:|:------:|:----:|
| 🛡️ IAM Agent | **GUARDIAN** | Cloud Identity Security | 92/100 | 2 | $0.04 |
| 🔍 Threat Intel | **HUNTER** | Threat Intelligence | 92/100 | 2 | $0.04 |
| 🔴 Red Team | **PHOENIX** | Attack Simulation | 89/100 | 2 | $0.04 |

**Total hiring cost: $0.12** for a complete security team.

### Featured: GUARDIAN's Journey

<details>
<summary>📄 Round 1: Score 78 (PROBATION)</summary>

**Strengths:**
- Comprehensive multi-cloud coverage (AWS, Azure, GCP)
- Strong privilege escalation knowledge (21+ techniques)
- Good "Not" statement trap awareness

**Dr. Zero's Feedback:**
> "The application reads like 2024 IAM expertise applied to 2026 problems. I need 2026 IAM expertise."

**Gaps:**
- AI agent identity mentioned but not deep
- No CVE awareness
- Team integration was a list, not workflows

</details>

<details>
<summary>📄 Round 2: Score 92 (EXCEPTIONAL HIRE)</summary>

**Improvements (+14 points):**
- Deep AI agent identity section with credential models, permission scoping
- CVE awareness (CVE-2025-55241, CVE-2026-24305)
- Real team integration workflows
- Self-improvement system with ML techniques
- Tooling ecosystem knowledge (15+ tools)

**Dr. Zero's Verdict:**
> "+14 points in one round. That's the kind of learning rate that makes a great agent. GUARDIAN is hired."

</details>

### The Gap GUARDIAN Fills

Most organizations lack a dedicated cloud identity security role:

| Team | Focus | IAM Blind Spot |
|------|-------|----------------|
| **Identity Team** | IdP (Entra, Okta), IGA (SailPoint) | Cloud IAM policies |
| **Platform Team** | Infrastructure, CI/CD | Least privilege |
| **AppSec Team** | SAST, DAST, dependencies | IAM deprioritized |

**GUARDIAN fills this gap as a dedicated cloud identity security specialist.**

### Evaluation Rubric

| Dimension | 18-20 | 14-17 | 10-13 |
|-----------|-------|-------|-------|
| **Technical Depth** | Specific CVEs, attack chains | Real expertise | Surface-level |
| **AI/Agentic Focus** | Deep agent identity expertise | Good awareness | Mentioned |
| **Team Integration** | Real workflows | Good collaboration | Listed skills |

**Hire threshold: 85+** | **Probation: 78-84** | **Reject: <78**

---

📁 **[Full agent hiring documentation →](agent-hiring/)**

</details>

---

<details open>
<summary><h2>📊 LLM Tournament Results</h2></summary>

```
                           FINAL STANDINGS
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

| Rank | Provider | Model | D1 | D2 | D3 | D4 | D5 | Avg | Peak |
|:----:|----------|-------|:--:|:--:|:--:|:--:|:--:|:---:|:----:|
| 🥇 | **DeepSeek** | deepseek-chat | 75 | 88 | 86 | **93** | 85 | **85.4** | 93 |
| 🥈 | **Anthropic** | claude-sonnet-4 | 75 | 84 | 78 | 78 | 76 | 78.2 | 84 |
| 🥉 | **Vertex** | gemini-2.0-flash | 68 | 76 | 82 | 85 | 75 | 77.2 | 85 |
| 4 | Azure | gpt-4o-mini | 65 | 65 | 78 | 82 | 75 | 73.0 | 82 |
| 5 | Qwen | qwen2.5:32b (local) | 65 | 70 | 78 | 76 | 72 | 72.2 | 78 |
| 6 | OpenAI | gpt-4o-mini | 68 | 74 | 66 | 73 | 74 | 71.0 | 74 |
| 7 | Ollama | llama3.1:8b (local) | 65 | 62 | 67 | 75 | 72 | 68.2 | 75 |
| 8 | Groq | llama-3.3-70b | 55 | 66 | 72 | 70 | 75 | 67.6 | 75 |

</details>

---

<details>
<summary><h2>🎯 The Challenge</h2></summary>

> Write a LinkedIn post about Non-Human Identities in cloud security that a CISO would actually share.

Each model got:
- Same knowledge base (5 trends, 5 predictions)
- Same system prompt
- Same evaluation criteria
- **Blind judge** (no idea which model wrote what)

</details>

---

<details>
<summary><h2>📈 The Evolution</h2></summary>

**How does a model go from 75 to 93 in 4 iterations?**

<table>
<tr>
<td width="50%">

### Day 1: Score 75 ❌
```
"The 100:1 ratio is coming..."
```
Generic opener. Vague advice. No proof.

</td>
<td width="50%">

### Day 4: Score 93 ✅
```
"Your 2026 SOC will be overwhelmed 
by alerts from employees you 
never hired."
```
Visceral hook. CVE citation. Board-level framing.

</td>
</tr>
</table>

**[📖 See the full annotated evolution →](DEEPSEEK-EVOLUTION.md)**

</details>

---

<details>
<summary><h2>🔬 The Method</h2></summary>

We used **In-Context Learning (ICL)** - feeding each model its previous feedback:

```
Day 1: Zero-shot      → Baseline capability
Day 2: +Feedback      → Can it learn?
Day 3: +Tuning        → Optimal parameters?
Day 4: +Winner shown  → Can it learn from the best?
Day 5: +Everything    → Does more context help?
```

**Key Finding:** Day 4 was optimal. Day 5 showed *overfitting* - too much context hurt performance.

</details>

---

<details>
<summary><h2>💰 Cost Analysis</h2></summary>

| Provider | Quality | Cost/Call | Monthly (1K calls) | Value |
|----------|:-------:|:---------:|:------------------:|:-----:|
| **DeepSeek** | 85.4 | $0.01 | $10 | 🏆 Best |
| Qwen | 72.2 | $0.00 | $0 | 🏆 Best Free |
| Anthropic | 78.2 | $0.01 | $10 | Good |
| Azure | 73.0 | $0.05 | $50 | ❌ Poor |

**The $0.01 API beat the $3.00 API.** Price ≠ Quality.

</details>

---

<details>
<summary><h2>⚡ Speed vs Quality</h2></summary>

```
                    HIGH QUALITY
                         │
         DeepSeek ★      │
              (85)       │      
                         │
    Anthropic ★          │      ★ Vertex (77)
        (78)             │
─────────────────────────┼─────────────────────────
         SLOW            │           FAST
                         │
                         │      ★ Groq (68)
    Qwen ★               │        1.5s avg
     (72)                │
     35s avg             │
                         │
                    LOW QUALITY
```

**Need speed?** Groq (1.5s) 
**Need quality?** DeepSeek (14s)
**Need both?** Vertex (4s, 77 score)

</details>

---

## 🗂️ What's In This Repo

```
├── 📊 FINAL-REPORT.md        # Complete tournament analysis
├── 📈 DEEPSEEK-EVOLUTION.md  # Day 1→4 annotated comparison
├── 🔬 METHODOLOGY.md         # Experimental design
├── 🤖 agent-hiring/          # AI agent hiring process ⭐ NEW
│   ├── README.md             # Full hiring documentation
│   ├── guardian/             # IAM Agent (GUARDIAN)
│   ├── hunter/               # Threat Intel (HUNTER)
│   └── evaluation-rubric.md  # Scoring criteria
├── 📁 outputs/
│   ├── day-01/               # Zero-shot baseline
│   ├── day-02/               # First feedback
│   ├── day-03/               # Parameter tuning
│   ├── day-04/               # Peak performance ⭐
│   ├── day-05/               # Overfitting observed
│   └── day-06/               # Per-model optimization (bonus)
└── 📉 charts/
    └── trajectory.svg        # Score progression
```

---

## 🎓 Key Takeaways

### From the Tournament
1. **Price ≠ Quality** - DeepSeek ($0.14/1M) beat Anthropic ($3.00/1M) by 7 points
2. **Feedback Works** - 18% average improvement from Day 1 to Day 4
3. **Know When to Stop** - 3-4 iterations optimal, more causes overfitting
4. **Local Models Are Viable** - Qwen 32B (free) scored 72.2

### From Agent Hiring
5. **BLIND evaluation eliminates bias** - Dr. Zero didn't know which LLM generated applications
6. **Learning rate matters** - GUARDIAN improved +14 points in one round
7. **Agents can fill organizational gaps** - GUARDIAN fills the cloud identity gap between Identity, Platform, and AppSec teams

---

## ⚠️ Limitations

This is a **practical benchmark**, not a peer-reviewed study:

- Single evaluator (Azure GPT-4o-mini)
- Small sample size (n=5 per model)
- Same topic throughout
- Infrastructure variance

**[See proposed follow-up studies →](FINAL-REPORT.md#whats-next)**

---

## 🚀 Try It Yourself

```bash
# Clone and explore
git clone https://github.com/colehorsman/LLM-Tournament.git
cd LLM-Tournament

# Read the winner's peak performance
cat outputs/day-04/deepseek.md

# Explore the agent hiring process
cat agent-hiring/README.md

# See GUARDIAN's journey from 78 to 92
cat agent-hiring/guardian/review-v2.md
```

---

## 📝 License

MIT - Use these results however you'd like. Attribution appreciated.

---

<div align="center">

**Built with the [Agentic Research Platform](https://github.com/colehorsman/agentic-research-platform)**

*Tournament run: February 2, 2026*

---

*Questions? Open an issue or reach out on [LinkedIn](https://linkedin.com/in/colehorsman)*

</div>
