# P2 Worked Example — Risk Classification Walkthrough: Vertrag.AI

**Project:** Pickles GmbH — AI Governance Framework
**Stage:** Phase 2 — Worked Example
**Document:** P2-Worked-Example-Risk-Classification-v1.md
**Status:** Draft
**Version:** v1
**Date:** 2026-02-28
**Assumptions:** Built on Phase 2 fictional system design — Vertrag.AI does not exist. All classification reasoning is illustrative. Not verified against real company data or reviewed by a qualified lawyer.

---

## About This Document

This document walks Vertrag.AI through the Pickles GmbH Risk Classification Framework (L1-3.2), making the decision-tree reasoning explicit at every step. The purpose is twofold: to assign a classification to Vertrag.AI for use across the Phase 2 worked example documents, and to demonstrate that the framework produces defensible, traceable reasoning when applied to a realistic system.

All classification decisions are flagged where professional legal review would be required before treating them as final.

---

## 1. System Under Review

| Field | Entry |
|---|---|
| **System** | Vertrag.AI |
| **System ID** | PKL-SYS-003 |
| **System Profile reference** | P2-Worked-Example-System-Profile-v1.md |
| **Classification conducted by** | [Governance function — fictional] |
| **Classification date** | 2026-02-28 |
| **Review required from** | Qualified German lawyer before operational use |

---

## 2. Decision Tree Walkthrough

The Pickles GmbH Risk Classification Framework uses a sequential decision tree. Each gate must be answered before proceeding. The first gate that results in a definitive classification terminates the tree; remaining gates are documented for completeness and audit traceability.

---

### Gate 1 — EU AI Act Prohibited Practices (Article 5)

**Question:** Does the system employ any AI practice prohibited under EU AI Act Article 5?

Prohibited practices under Article 5 include: subliminal manipulation, exploitation of vulnerabilities, real-time biometric surveillance in public spaces, social scoring by public authorities, and certain emotion recognition and biometric categorisation applications.

**Assessment for Vertrag.AI:**

Vertrag.AI analyses uploaded contract documents and produces redlined suggested amendments. It does not:
- Manipulate users subliminally or exploit psychological vulnerabilities
- Conduct any form of biometric processing
- Perform emotion recognition
- Operate as a social scoring mechanism
- Function autonomously in a manner that bypasses human will

None of the Article 5 prohibited categories apply to a contract review tool of this design.

**Decision:** ❌ No prohibited practice present → proceed to Gate 2

---

### Gate 2 — EU AI Act High-Risk Classification (Annex III)

**Question:** Does the system fall within one of the high-risk categories listed in EU AI Act Annex III?

Annex III lists eight areas of high-risk AI systems. The most relevant to a legal AI tool are examined below.

| Annex III Category | Description | Assessment for Vertrag.AI |
|---|---|---|
| 1 — Biometric systems | Remote biometric identification, categorisation | Not applicable — no biometric processing |
| 2 — Critical infrastructure | Safety components of critical infrastructure | Not applicable |
| 3 — Education and vocational training | Determining access to education, assessment of learners | Not applicable |
| 4 — Employment and workers management | Recruitment, promotion, task allocation, performance monitoring affecting employment | Not applicable — system reviews contracts, not employment decisions |
| 5 — Essential private and public services | Credit scoring, emergency services dispatch, risk assessment in life/health insurance | Potentially relevant: contract review could include financial contracts, insurance contracts, or credit agreements. Analysis below. |
| 6 — Law enforcement | Risk assessment of natural persons, polygraph, profiling | Not applicable — Vertrag.AI is not used by law enforcement |
| 7 — Migration, asylum, border control | Risk assessment, document authentication, visa applications | Not applicable |
| 8 — Administration of justice and democratic processes | AI assisting courts or tribunals; influencing elections | Potentially relevant: if Vertrag.AI output is used in litigation support or dispute resolution. Analysis below. |

**Detailed analysis — Annex III Category 5 (Essential private services):**

Annex III, point 5(b) covers AI systems used to evaluate creditworthiness or establish credit scores, except where used to detect financial fraud. Vertrag.AI reviews contracts that *may include* financial or credit agreements, but it does not itself score creditworthiness or make credit decisions. The system analyses the legal text of a contract and flags legal risk in the document — it does not produce a creditworthiness assessment of any natural person. On this basis, Category 5 does not apply to Vertrag.AI as designed.

However: if a future product iteration were to produce a risk score *about a counterparty* rather than a risk analysis *of a document*, this classification would need to be revisited. [Flag for product roadmap review.]

**Detailed analysis — Annex III Category 8 (Administration of justice):**

Annex III, point 8(a) covers AI systems intended to assist judicial authorities in researching and interpreting facts and law and applying the law to a concrete set of facts. Vertrag.AI is used by lawyers at law firms, not by courts or tribunals. Its output is an input to lawyer advice, not a direct input to judicial decision-making. On this basis, Category 8 does not apply in the system's current deployment context.

However: if Vertrag.AI output were used directly in court submissions without further independent legal analysis — for example, if a solicitor presented the AI redline as their own advice without review — this boundary would become less clear. The mandatory human review gate in the product design, and the explicit labelling of output as AI-drafted, are the key controls mitigating this risk. [Flag for legal review; reinforce in Human Oversight Policy application.]

**Decision:** ❌ No Annex III high-risk category confirmed → proceed to Gate 3

> **[LEGAL REVIEW FLAG]** The Annex III analysis above involves interpretive judgment on the scope of EU AI Act categories as applied to a contract review tool. This reasoning should be reviewed by a qualified lawyer with EU AI Act expertise before any final classification is relied upon operationally. EU AI Act guidance from the European AI Office may also provide further clarity as it develops.

---

### Gate 3 — General Purpose AI (GPAI) Model Assessment (Articles 51–55)

**Question:** Is Vertrag.AI itself a General Purpose AI model, or does it deploy one in a way that requires specific GPAI obligations?

Vertrag.AI is a *deployer* of a GPAI model (the Claude API, provided by Anthropic). Anthropic, as the provider of the underlying Claude model, holds the GPAI provider obligations under Articles 51–55 of the EU AI Act. Pickles GmbH, as deployer, is not a GPAI provider and does not trigger GPAI provider obligations.

Pickles GmbH does, however, have provider obligations under Article 16 (as provider of Vertrag.AI — applied voluntarily at the Medium-High internal tier) and transparency obligations under Article 50. Law firm clients who license Vertrag.AI are deployers under Article 3(4) and hold obligations under Article 26.

**Decision:** ✅ Pickles GmbH is not a GPAI provider → GPAI provider obligations do not apply → proceed to Gate 4

> **Role clarification:** At the GPAI layer, Pickles GmbH is a downstream user of Anthropic's Claude model. At the Vertrag.AI product layer, Pickles GmbH is the **provider** of Vertrag.AI under Article 3(3). Law firm clients are **deployers** of Vertrag.AI under Article 3(4). These are distinct roles at different layers of the AI value chain.

---

### Gate 4 — Transparency Obligations (Article 50)

**Question:** Does the system trigger transparency obligations under EU AI Act Article 50?

Article 50 obligations apply to:
- AI systems that interact with natural persons (chatbot disclosure requirement)
- AI systems that generate synthetic content (deepfake disclosure)
- Emotion recognition systems
- Biometric categorisation systems

Vertrag.AI produces AI-generated contract analysis and clause suggestions. The output is reviewed by a lawyer before reaching any client. The system does not directly interact with natural persons (law firm clients); it interacts with qualified lawyers as professional users.

**Assessment:**

Article 50(1) (chatbot disclosure) — Lawyers using Vertrag.AI are natural persons, and Article 50(1) applies in principle. However, the obligation does not apply where the AI nature of the interaction is obvious from the context. In a professional B2B tool explicitly marketed and used as an AI contract review system, the AI nature of the interaction is apparent to a reasonably informed professional user. The obligation is therefore unlikely to apply in the standard interface. Note: if a client-facing conversational interface is added, Article 50(1) disclosure would need to be assessed interface-by-interface.

Article 50(4) (deployer synthetic content disclosure) may apply to law firm clients who share AI-drafted clause suggestions with their own clients, to the extent those suggestions constitute AI-generated text that could be presented as human-authored. The mandatory output labelling in the product design (all AI-generated amendments marked as AI-drafted) supports compliance with this obligation by law firm deployers. [Flag for legal review — whether Article 50(4) applies to AI-generated contract clauses and what disclosure form is required.]

**Decision:** ✅ Article 50 transparency obligations apply — specifically Article 50(1) (low risk; AI nature likely obvious from context) and Article 50(2) (machine-readable labelling — gap, not yet addressed) → to be addressed in Transparency & Disclosure Framework

---

### Gate 5 — Internal Risk Criteria

Having completed the regulatory gates, the system is now assessed against Pickles GmbH's internal risk criteria to assign an internal tier.

**Internal criteria assessment:**

| Criterion | Weight | Assessment | Score |
|---|---|---|---|
| Impact on legal outcomes affecting natural persons | High | High — contract review directly influences advice given to clients on legally binding documents | ⬆ Elevates |
| Level of automation in output | High | Medium — output requires mandatory lawyer review; no autonomous action | → Neutral |
| Client-facing exposure | High | Indirect — output goes to lawyer, not directly to client | → Neutral |
| Processing of legally privileged material | Medium | High — all uploaded contracts are likely privileged material | ⬆ Elevates |
| Processing of personal data | Medium | High — contracts frequently contain personal data of third parties | ⬆ Elevates |
| Professional regulatory overlay | Medium | High — BRAK obligations on lawyers using AI; professional liability consequences | ⬆ Elevates |
| RAG dependency risk | Medium | Medium — output quality dependent on corpus accuracy and freshness | ⬆ Elevates |
| Third-party model provider dependency | Low | Present — Claude API; DPA required; model updates must be managed | ⬆ Elevates |

**Aggregate assessment:** Multiple elevating factors with no strong mitigating factors. The mandatory human review gate is the single most significant risk control and prevents classification as High risk, but it does not reduce the system to Low risk given the professional liability context and data sensitivity.

---

## 3. Classification Result

### 3.1 EU AI Act Classification

| Dimension | Classification | Basis |
|---|---|---|
| **EU AI Act risk tier** | **Limited risk** | Does not fall within Annex III; no prohibited practice; Article 50 transparency obligations apply |
| **Primary obligation** | Transparency (Article 50) — labelling of AI-generated output; chatbot disclosure (low risk — AI nature likely obvious) | Addressed in product design via AI-drafted output marking |
| **Secondary obligation** | Provider obligations under Article 16 applied voluntarily at Medium-High internal tier; law firm clients hold deployer obligations under Article 26 | To be confirmed on legal review |
| **GPAI downstream obligations** | Applicable — Pickles GmbH uses a GPAI model (Claude API); Anthropic holds Articles 51–55 obligations as GPAI provider | See GPAI provisions and Section 2.5 of P2-Worked-Example-EU-AI-Act-Mapping-v1.md |

> **Conditional flag:** If the EU AI Act classification is revisited and Annex III Category 5 or 8 is found to apply, the system would become a High Risk AI system subject to the full suite of Chapter III Section 2 obligations (conformity assessment, technical documentation, human oversight requirements, registration, etc.). This document should be rerun through the decision tree if the product design or deployment context changes materially.

### 3.2 Pickles GmbH Internal Classification

| Dimension | Classification |
|---|---|
| **Internal tier** | **Medium-High** |
| **Tier definition** | Decision-support AI system in a regulated professional context, processing sensitive data, with indirect client exposure and professional liability consequences |
| **Required documentation** | Full technical documentation pack; DPIA; vendor risk assessment; monitoring framework entry |
| **Required review level** | Head of Product sign-off; Legal Counsel sign-off; qualified lawyer review of EU AI Act classification |
| **Monitoring intensity** | Active — quarterly monitoring review; error and complaint tracking; RAG corpus refresh on defined schedule |
| **Escalation pathway** | Product incident → Head of Product → Legal Counsel → CEO if regulatory dimension |

### 3.3 Classification Summary

```
Vertrag.AI — PKL-SYS-003

EU AI Act:   Limited Risk (Article 50 transparency obligations)
             Pickles GmbH = provider of Vertrag.AI (Article 3(3))
             Law firm clients = deployers of Vertrag.AI (Article 3(4))
Internal:    Medium-High
             ↓
Obligations triggered:
  • AI-generated output labelling (Article 50)
  • Provider obligations (Article 16 — applied voluntarily at Medium-High tier)
  • Full technical documentation
  • DPIA required
  • Vendor/model risk assessment required
  • Active monitoring programme
  • Mandatory human oversight gate (existing product design)

Legal review required before classification is treated as final.
```

---

## 4. What This Classification Means for Subsequent Documents

The classification result feeds directly into the remaining Phase 2 worked example documents:

| Document | Impact of Classification |
|---|---|
| P2-Worked-Example-EU-AI-Act-Mapping-v1.md | Article 50 obligations mapped in full; provider obligations under Article 16 included (applied voluntarily); Annex III analysis documented |
| P2-Worked-Example-Technical-Documentation-v1.md | Full technical documentation pack required at Medium-High tier |
| P2-Worked-Example-Monitoring-Entry-v1.md | Active monitoring tier applies; quarterly review cycle; defined metrics |

---

## 5. Open Items and Review Flags

| # | Item | Action Required | Owner |
|---|---|---|---|
| RC-001 | EU AI Act Annex III analysis — interpretive judgment on Categories 5 and 8 | Legal review before classification treated as final | Qualified German lawyer |
| RC-002 | Article 50(4) applicability to AI-generated contract clause suggestions (law firm deployer disclosure obligation) | Legal review of disclosure form required | Legal Counsel |
| RC-003 | Product roadmap check — any planned feature increasing automation level | Reassessment if automation level rises | Head of Product |
| RC-004 | Provider obligations under Article 16 — precise scope at limited-risk tier (voluntary application) | Legal review | Legal Counsel |
| RC-005 | EU AI Office guidance on GPAI deployer obligations | Monitor for updated guidance as EU AI Act implementation matures | Governance function |

---

*This document is a fictional worked example produced for educational and demonstration purposes. Vertrag.AI does not exist. All regulatory analysis is illustrative and does not constitute legal advice. Professional legal review is required before any classification is relied upon operationally.*
