# P2 Worked Example — Monitoring Framework Entry: Vertrag.AI

**Project:** Pickles GmbH — AI Governance Framework
**Stage:** Phase 2 — Worked Example
**Document:** P2-Worked-Example-Monitoring-Entry-v1.md
**Status:** Draft
**Version:** v1
**Date:** 2026-02-28
**Assumptions:** Built on Phase 2 fictional system design — Vertrag.AI does not exist. All metrics, thresholds, and dashboard designs are illustrative. Requires population with real operational data before use.

---

## About This Document

This document populates the Pickles GmbH AI Monitoring Framework (L3-6.1) with a fully worked entry for Vertrag.AI. It defines the specific metrics to be tracked, how they are measured, what thresholds trigger action, the review cadence, and the dashboard design for this system.

The monitoring design reflects Vertrag.AI's internal classification as Medium-High risk, professional liability exposure, and the particular challenge of monitoring an AI system that processes legally privileged material — which limits what can be logged.

---

## 1. System Reference

| Field | Entry |
|---|---|
| **System** | Vertrag.AI |
| **System ID** | PKL-SYS-003 |
| **Internal risk tier** | Medium-High |
| **Monitoring tier** | Active — quarterly formal review; continuous automated monitoring |
| **Monitoring owner** | Head of Product |
| **Technical monitoring lead** | Head of Engineering |
| **Entry last reviewed** | 2026-02-28 (initial) |

---

## 2. Monitoring Constraints

Before defining metrics, the key constraint shaping Vertrag.AI's monitoring design must be stated clearly.

**The GDPR/confidentiality constraint:** Contract documents uploaded to Vertrag.AI are legally privileged material and contain personal data. Full contract text, full prompt content, and matter-identifying information cannot be retained in monitoring logs. This means standard LLM monitoring techniques — such as reviewing full prompt/completion pairs for quality — are not available.

This constraint is inherent to the legal market context and cannot be resolved without compromising the confidentiality obligations that make the product viable. The monitoring design works around it through:

- **Metadata-only logging** — events and outcomes are logged without content
- **Sampled review** — a small, consented sample of sessions used for quality testing
- **Outcome-based signals** — lawyer accept/reject patterns as a proxy for output quality
- **User-reported signals** — structured error and concern reporting by lawyers

All monitoring design decisions below reflect this constraint.

---

## 3. Metrics Register

### 3.1 Output Quality Metrics

| Metric ID | Metric Name | Description | Measurement Method | Frequency | Target | Alert Threshold |
|---|---|---|---|---|---|---|
| MQ-01 | Suggestion acceptance rate | Percentage of AI-generated redline suggestions accepted by reviewing lawyers without modification | Derived from review action logs (accept/reject/modify counts per session) | Continuous; weekly aggregate | ≥60% acceptance [ASSUMPTION: baseline to be established in first 90 days] | <40% acceptance in any rolling 7-day window |
| MQ-02 | Suggestion modification rate | Percentage of accepted suggestions that were modified before acceptance | Derived from review action logs | Weekly aggregate | Informational only — no threshold initially | Significant change from baseline (>±15%) |
| MQ-03 | Clause identification miss rate (user-reported) | Number of sessions where lawyer reports a significant clause issue was missed by the system | User-reported via in-product feedback mechanism | Per report; monthly aggregate | 0 per month [ASSUMPTION] | Any single report triggers review; ≥3 in a month triggers incident |
| MQ-04 | Citation accuracy (sampled) | Percentage of specific legal provision citations (BGB articles, AGB standards) that are accurate when spot-checked | Quarterly sampled review by legal content team — minimum 20 sessions reviewed | Quarterly | ≥95% accuracy on cited provisions | <90% triggers urgent review and potential system suspension |
| MQ-05 | False positive rate (sampled) | Percentage of suggestions in sampled sessions assessed as spurious by reviewing lawyers | Quarterly sampled review | Quarterly | ≤15% of suggestions assessed as spurious | >25% triggers product review |

**Note on sampling:** Quarterly sampled reviews (MQ-04, MQ-05) require law firm users to opt in to having a session reviewed by Pickles GmbH's legal content team. Session content reviewed under sampling must be subject to confidentiality obligations equivalent to those governing the original matter. Consent and confidentiality framework for sampling must be established before this metric can be collected. [ASSUMPTION: consent framework does not yet exist — flag for Legal Counsel.]

---

### 3.2 System Performance Metrics

| Metric ID | Metric Name | Description | Measurement Method | Frequency | Target | Alert Threshold |
|---|---|---|---|---|---|---|
| SP-01 | API error rate | Percentage of Anthropic API calls that return an error or timeout | Application error logs | Continuous | <1% error rate | >3% in any 1-hour window |
| SP-02 | Processing latency (p95) | 95th percentile end-to-end processing time from upload to redlined output available | Application performance logs | Continuous | <120 seconds [ASSUMPTION] | >300 seconds sustained for >30 minutes |
| SP-03 | RAG retrieval failure rate | Percentage of queries where RAG layer returns zero relevant results | RAG system logs | Continuous | <2% of queries | >5% in any 24-hour window |
| SP-04 | Document processing failure rate | Percentage of uploaded documents that fail to parse or process | Application error logs | Continuous | <0.5% | >2% triggers engineering review |
| SP-05 | System availability | Uptime percentage measured against agreed SLA | Infrastructure monitoring | Continuous | ≥99.5% monthly [ASSUMPTION] | Any unplanned downtime >2 hours triggers incident log entry |

---

### 3.3 Usage and Adoption Metrics

These metrics are informational — they support product understanding and help contextualise quality signals rather than triggering direct governance actions.

| Metric ID | Metric Name | Description | Frequency |
|---|---|---|---|
| UA-01 | Active law firm accounts | Number of firms with at least one session in the period | Monthly |
| UA-02 | Sessions per firm | Average sessions per active firm per month | Monthly |
| UA-03 | Contract types processed | Distribution of contract categories processed (commercial, employment, real estate, etc.) | Quarterly |
| UA-04 | Rejection-only sessions | Sessions where the lawyer rejected all AI suggestions — potential indicator of poor output or inappropriate use case | Monthly |
| UA-05 | Pre-signature vs post-signature split | Proportion of sessions in each use case | Monthly |

---

### 3.4 User-Reported Signal Metrics

| Metric ID | Metric Name | Description | Measurement Method | Frequency | Alert Threshold |
|---|---|---|---|---|---|
| UR-01 | User error reports | Structured reports submitted by lawyers via in-product feedback on output quality issues | In-product report form; tracked in issue log | Per report; monthly aggregate | Any report categorised as "material error with client impact" triggers incident review |
| UR-02 | Support tickets related to output quality | Help desk tickets where the reported issue relates to AI output accuracy or relevance | Support ticket tagging | Monthly | ≥3 in a month triggers product review |
| UR-03 | Net Promoter Score (NPS) — governance signal | NPS data filtered for comments mentioning accuracy, reliability, or trust | Quarterly NPS survey | Quarterly | Significant drop (>10 points) or cluster of negative accuracy comments triggers review |

---

### 3.5 Model and Infrastructure Change Signals

| Metric ID | Metric Name | Description | Measurement Method | Frequency |
|---|---|---|---|---|
| MC-01 | Model version in use | Current Claude model version deployed | Deployment log | Continuous — logged on change |
| MC-02 | RAG corpus version | Current version of German legal knowledge base | Knowledge base version log | Continuous — logged on update |
| MC-03 | Post-change quality delta | Change in MQ-01 (acceptance rate) in 30 days following any model or corpus change | Derived from MQ-01 data, segmented by deployment date | Within 30 days of any change |
| MC-04 | Prompt version | Current system prompt version in production | Deployment log | Continuous — logged on change |

---

## 4. Review Cadence

| Review Type | Frequency | Trigger | Participants | Output |
|---|---|---|---|---|
| Automated alert review | As triggered | Alert threshold breached (see Section 3) | Head of Engineering; on-call engineer | Incident log entry or resolution note |
| Weekly metrics review | Weekly | Standing | Head of Product | Dashboard review; flag anomalies |
| Monthly monitoring report | Monthly | Calendar | Head of Product; Head of Engineering | Written summary of MQ, SP, UR metrics; trends; any open issues |
| Quarterly formal review | Quarterly | Calendar | Head of Product; Head of Engineering; Legal Counsel | Full review of all metrics including sampled quality review (MQ-04, MQ-05); review of assumptions; update monitoring entry if thresholds need adjustment |
| Post-incident review | Within 14 days of any incident | Incident closure | Head of Product; Head of Engineering; Legal Counsel (if legal dimension) | Root cause analysis; corrective actions; monitoring update if gaps identified |
| Post-change review | 30 days after model or corpus change | MC-03 trigger | Head of Product; Head of Engineering | Quality delta assessment; decision to maintain, adjust, or rollback |

---

## 5. Dashboard Design

### 5.1 Dashboard Purpose and Audience

The Vertrag.AI monitoring dashboard provides a single-view summary of system health for the Head of Product and Head of Engineering. It is not a client-facing document. It feeds into the monthly monitoring report and quarterly formal review.

### 5.2 Dashboard Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  VERTRAG.AI — MONITORING DASHBOARD          [Last updated: live] │
├─────────────────────────────────────────────────────────────────┤
│  SYSTEM STATUS          │  MODEL VERSION      │  CORPUS VERSION  │
│  ● OPERATIONAL          │  claude-sonnet-4-6  │  v1.2 (Feb 2026) │
├───────────────────────────────────────┬─────────────────────────┤
│  OUTPUT QUALITY                       │  SYSTEM PERFORMANCE      │
│                                       │                          │
│  Suggestion acceptance rate (7d)      │  API error rate (24h)    │
│  ████████████░░  64%  ✓               │  0.4%  ✓                 │
│                                       │                          │
│  User error reports (30d)             │  Processing latency p95  │
│  2 reports — 0 material  ✓            │  87s  ✓                  │
│                                       │                          │
│  Citation accuracy (last sample)      │  RAG retrieval failures  │
│  97%  ✓  [Q4 2025]                    │  1.1%  ✓                 │
│                                       │                          │
│  False positive rate (last sample)    │  System availability     │
│  11%  ✓  [Q4 2025]                    │  99.8%  ✓                │
├───────────────────────────────────────┴─────────────────────────┤
│  TREND — SUGGESTION ACCEPTANCE RATE (12 weeks)                   │
│                                                                  │
│  70% ┤                                                           │
│  65% ┤    ●   ●       ●   ●   ●                                  │
│  60% ┤●       ●   ●       ●       ●   ●                          │
│  55% ┤                                ●                          │
│  50% ┤                                                           │
│      └──────────────────────────────────────────────────────    │
│        W1  W2  W3  W4  W5  W6  W7  W8  W9  W10 W11 W12          │
│                                                 ↑ alert zone     │
├─────────────────────────────────────────────────────────────────┤
│  OPEN ALERTS          │  NEXT REVIEW                             │
│  None                 │  Monthly: 31 Mar 2026                    │
│                       │  Quarterly: 30 Apr 2026                  │
│                       │  Sampled review due: 30 Apr 2026         │
└─────────────────────────────────────────────────────────────────┘
```

**[ASSUMPTION]** Dashboard above is illustrative. Technical implementation (tooling, data connections, refresh frequency) to be confirmed by engineering team. Candidate tooling includes internal BI dashboard, Grafana, or a purpose-built product health screen within the Pickles GmbH operations interface.

### 5.3 Alert States

| Status | Indicator | Meaning |
|---|---|---|
| ✓ | Green — within target | No action required |
| ⚠ | Amber — approaching threshold | Monitor closely; review at next scheduled meeting |
| ✗ | Red — threshold breached | Immediate review required; escalate per incident response playbook (L3-6.2) |

---

## 6. Monitoring Gaps and Open Actions

| # | Gap | Priority | Owner | Action |
|---|---|---|---|---|
| MON-001 | Consent and confidentiality framework for sampled quality review (MQ-04, MQ-05) not yet established | High | Legal Counsel | Design consent model for sampling; obtain legal sign-off before quarterly sampled review begins |
| MON-002 | Baseline acceptance rate (MQ-01 target) not yet established — no production data | High | Head of Product | Run 90-day baseline period before alert threshold is enforced; set threshold from baseline data |
| MON-003 | In-product user error report mechanism not yet confirmed | Medium | Head of Product / Engineering | Confirm UR-01 and UR-02 reporting mechanisms are built into product |
| MON-004 | Dashboard tooling not yet selected or implemented | Medium | Head of Engineering | Select tooling; implement initial dashboard before system goes live |
| MON-005 | RAG corpus version control logging not yet confirmed | Medium | Head of Engineering | Confirm MC-02 logging is implemented; version history maintained |

---

## 7. Connection to Other Governance Documents

| Area | Document |
|---|---|
| Incident response (when thresholds are breached) | L3-6.2-Incident-Response-Playbook-v1.md |
| Model change management (MC-01 to MC-04) | L3-6.3-Model-Change-Management-Protocol-v1.md |
| Testing methodology (MQ-04, MQ-05 sampled reviews) | P2-Worked-Example-Technical-Documentation-v1.md Section 4 |
| Human oversight design (MQ-01 to MQ-03 depend on) | L1-3.4-Human-Oversight-Policy-v1.md |
| GDPR logging constraints (Section 2) | L2-5.1-Data-Flow-Map-v1.md; L2-5.2-DPIA-Assessment-v1.md |

---

*This document is a fictional worked example produced for educational and demonstration purposes. Vertrag.AI does not exist. All metrics, thresholds, and dashboard designs are illustrative and do not constitute operational monitoring specifications. Professional review is required before any monitoring framework is applied operationally.*
