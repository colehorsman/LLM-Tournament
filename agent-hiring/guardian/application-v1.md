# GUARDIAN - Round 1 Application (Zero-Shot)

**Applicant**: GUARDIAN  
**Model**: DeepSeek V3  
**Position**: Cloud Identity & Access Management Agent  
**Round**: 1 (Zero-Shot - No Prior Feedback)  
**Score**: 78/100 (PROBATION)

---

## Position Understanding

I am applying for the IAM Agent position on the Platform Security team. In 2026, identity is not just a security control—it's the primary attack surface. With non-human identities outnumbering humans 80:1 and AI agents requiring privileged access to function, traditional IAM approaches are insufficient.

---

## Core Capabilities

### Multi-Cloud IAM Policy Analysis

| Provider | Components Covered |
|----------|-------------------|
| **AWS** | Identity policies, resource policies, permission boundaries, SCPs, RCPs, session policies, trust policies |
| **Azure** | Entra ID roles, Azure RBAC, PIM, Conditional Access, workload identity federation, managed identities |
| **GCP** | IAM policies, custom roles, service accounts, workload identity federation, org policies |

### Critical Patterns I Detect

```
DANGEROUS: "Effect": "Allow", "Action": "*", "Resource": "*"
DANGEROUS: "Effect": "Allow", "Action": "iam:*"
SUBTLE: "NotAction" with "Allow" (inverse logic trap)
SUBTLE: "NotResource" with "Allow" (scope expansion)
SUBTLE: Condition keys that can be spoofed (aws:SourceIp in Lambda)
```

### Privilege Escalation Detection

**AWS**: 21+ known techniques (CreatePolicyVersion, PassRole chains, etc.)  
**Azure**: 10+ paths (Application Admin abuse, Intune escalation, etc.)  
**GCP**: 13+ techniques (setIamPolicy, service account key creation, etc.)

### The "Not" Statement Trap

```json
// DANGEROUS: This ALLOWS everything EXCEPT ec2:TerminateInstances
{
  "Effect": "Allow",
  "NotAction": "ec2:TerminateInstances",
  "Resource": "*"
}
// Result: User can do iam:*, s3:*, lambda:*, etc.
```

### Policy Simulation

```
Evaluation Order:
1. Explicit Deny → DENY
2. Organization SCP → must ALLOW
3. Resource Control Policy → must ALLOW
4. Permission Boundary → must ALLOW
5. Session Policy → must ALLOW
6. Identity Policy → must ALLOW
7. Resource Policy → can ALLOW
8. Default → IMPLICIT_DENY
```

---

## NHI Management

| Category | Examples | Risk Factors |
|----------|----------|--------------|
| Service Accounts | AWS IAM roles, GCP SAs, Azure SPs | Long-lived, over-privileged |
| API Keys | REST API keys, SDK credentials | No rotation, no scope |
| AI Agent Identities | LLM agents, automation bots | New category, undefined |

---

## Team Integration

| Agent | Relationship | Data Flow |
|-------|--------------|-----------|
| Red Team Agent | Bidirectional | Priv esc paths ↔ Attack validation |
| UEBA Agent | Outbound | Identity baselines → Anomaly detection |
| Threat Intel | Inbound | Actor TTPs → Identity-based IOCs |

### A2A Skills Exposed

- `analyze-iam-policy`
- `detect-priv-esc`
- `simulate-access`
- `recommend-least-priv`
- `audit-nhi`
- `cross-cloud-map`

---

## Metrics

| Metric | Target |
|--------|--------|
| Policies Analyzed | 500+/day |
| Priv Esc Paths Found | 10+/week |
| False Positive Rate | <15% |
| Remediation Adoption | 70%+ |
| NHI Coverage | 95%+ |

---

## Closing Statement

Identity is the new perimeter. In 2026, with AI agents requiring privileged access and NHIs outnumbering humans 80:1, traditional IAM is insufficient.

I am GUARDIAN. I protect the identities that protect everything else.

---

*Application submitted: 2026-02-08*
