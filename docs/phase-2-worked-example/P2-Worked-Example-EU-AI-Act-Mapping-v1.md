# P2 Worked Example — EU AI Act Mapping: Vertrag.AI

**Project:** Pickles GmbH — AI Governance Framework
**Stage:** Phase 2 — Worked Example
**Document:** P2-Worked-Example-EU-AI-Act-Mapping-v1.md
**Status:** Draft
**Version:** v1
**Date:** 2026-02-28
**Assumptions:** Built on Phase 2 fictional system design — Vertrag.AI does not exist. All regulatory analysis is illustrative. Not verified against real company data or reviewed by a qualified lawyer.

---

## About This Document

This document maps Vertrag.AI against the applicable provisions of Regulation (EU) 2024/1689 (the EU AI Act). It draws on the classification established in P2-Worked-Example-Risk-Classification-v1.md and populates the mapping matrix format defined in L2-4.1-EU-AI-Act-Risk-Mapping-Matrix-v1.md with specific content for this system.

The document is structured in three parts:

1. Applicable provisions matrix — articles that apply to Vertrag.AI, with obligations and current status
2. Non-applicable provisions — Annex III and other provisions assessed and confirmed as not applicable, with reasoning
3. Compliance gap analysis — obligations not yet fully addressed and actions required

All article references are to Regulation (EU) 2024/1689 as published in the Official Journal of the European Union (OJ L, 2024/1689, 12.7.2024).

---

## 1. System and Classification Reference

| Field | Entry |
|---|---|
| **System** | Vertrag.AI |
| **System ID** | PKL-SYS-003 |
| **EU AI Act classification** | Limited risk (Article 50 transparency obligations) |
| **Pickles GmbH internal tier** | Medium-High |
| **Pickles GmbH role** | Provider of Vertrag.AI (Article 3(3)) |
| **Law firm customer role** | Deployer of Vertrag.AI (Article 3(4)) |
| **Anthropic role** | Provider of upstream GPAI model (Claude API) — Articles 51–55 |
| **Classification source document** | P2-Worked-Example-Risk-Classification-v1.md |
| **Legal review required** | Yes — before classification and obligations are treated as final |

---

## 2. Applicable Provisions Matrix

### 2.1 General Provisions

| Article | Title / Subject | Obligation for Pickles GmbH | Status | Notes |
|---|---|---|---|---|
| Article 3(3) | Definition — provider | Pickles GmbH develops Vertrag.AI and places it on the market under its own name or trademark | Confirmed | Pickles GmbH is the provider of Vertrag.AI. Anthropic is the provider of the upstream Claude GPAI model. Law firm clients are deployers of Vertrag.AI (Article 3(4)). |
| Article 3(4) | Definition — deployer | Law firm clients who license Vertrag.AI use the system under their authority for professional contract review | Confirmed | Pickles GmbH, as provider, uses the Claude API (a GPAI model) as an upstream component of Vertrag.AI — at the GPAI layer Pickles GmbH is a downstream user, but at the product layer it is the provider. |
| Article 3(8) | Definition — intended purpose | System must be operated within its intended purpose as defined by Pickles GmbH | Confirmed | Intended purpose documented in system profile (P2-Worked-Example-System-Profile-v1.md) |
| Article 4 | AI literacy | Deployers must ensure staff working with AI systems have sufficient AI literacy | Partially addressed | [ASSUMPTION] Training programme not yet confirmed; flag for HR/product team |

---

### 2.2 Transparency Obligations (Article 50)

This is the primary regulatory article applicable to Vertrag.AI at its current risk classification.

| Sub-article | Obligation | How Addressed by Vertrag.AI | Status | Gap / Action |
|---|---|---|---|---|
| Article 50(1) | Where an AI system interacts directly with natural persons, those persons must be informed they are interacting with an AI system, unless the AI nature is obvious from the context to a reasonably well-informed, observant and circumspect person | Lawyers using Vertrag.AI are natural persons; Article 50(1) applies in principle. In a professional B2B tool explicitly marketed and used as an AI contract review system, the AI nature of the interaction is apparent to a reasonably informed professional user. | Low risk — AI nature likely obvious from context; assess per interface | Monitor: if a client-facing conversational interface is added to the product, Article 50(1) disclosure would need to be assessed interface-by-interface |
| Article 50(3) | Deployers of emotion recognition or biometric categorisation systems must inform natural persons exposed to the operation of the system | Vertrag.AI does not perform emotion recognition or biometric categorisation | Not applicable | N/A |
| Article 50(4) | Deployers of AI systems that generate synthetic content (deep fakes; AI-generated text for public interest) must disclose that the content has been artificially generated or manipulated | Law firm clients (deployers) who share AI-drafted clause suggestions with their own clients may trigger Article 50(4) obligations. The mandatory output labelling in the product design (all AI-generated amendments marked as AI-drafted) supports deployer compliance. | Partially addressed (law firm deployer obligation) | **Gap:** The precise form of Article 50(4) disclosure required of law firm deployers — and whether the mandatory lawyer review constitutes sufficient editorial control for the safe harbour — requires legal review. Pickles GmbH should document guidance for law firm deployers on compliance with this obligation. |
| Article 50(2) | Providers of AI systems generating synthetic audio, image, video, or text content must ensure outputs are marked in a machine-readable format detectable as artificially generated | Vertrag.AI produces text output (redlined DOCX). Machine-readable marking of AI-generated text content may be required as a provider obligation. | **Gap — not yet addressed** | **Action:** Assess whether machine-readable marking is technically feasible in DOCX output format. Legal review required on scope of Article 50(2) for document-based AI output. |

---

### 2.3 Provider Obligations Applied Voluntarily (Article 16 — Good Practice at Limited-Risk Tier)

Article 16 sets out obligations for providers of high-risk AI systems. Vertrag.AI is classified as limited risk, so these obligations do not apply mandatorily. However, as provider of Vertrag.AI, Pickles GmbH applies several of these controls voluntarily at the Medium-High internal tier as a matter of good governance practice.

| Obligation | Article 16 Reference | Applicability to Vertrag.AI | Approach Taken |
|---|---|---|---|
| Technical documentation | Article 16(b), Article 11 | Mandatory for high-risk only; applied voluntarily at Medium-High internal tier | Full technical documentation produced — see P2-Worked-Example-Technical-Documentation-v1.md |
| Logging and traceability | Article 16(c), Article 12 | Mandatory for high-risk only; applied voluntarily | Session-level audit logging implemented [ASSUMPTION] |
| Transparency to deployers | Article 16(d), Article 13 | Mandatory for high-risk only; applied voluntarily at Medium-High tier. As provider, Pickles GmbH provides instructions for use to law firm deployers documenting the system's intended purpose, capabilities, limitations, and human oversight requirements. | See L2-4.3-Transparency-Disclosure-Framework-v1.md |
| Human oversight measures | Article 16(f), Article 14 | Mandatory for high-risk only; applied as core product design principle | Mandatory lawyer review gate; see Human Oversight Policy (L1-3.4) |
| Accuracy, robustness, cybersecurity | Article 16(g), Article 15 | Mandatory for high-risk only; applied as operational standard | Addressed in monitoring framework and model change management protocol |

---

### 2.4 Obligations Applicable to Deployers Generally (Article 26)

Article 26 sets out obligations for deployers of AI systems. As provider of Vertrag.AI, Pickles GmbH is not subject to Article 26 directly — these obligations apply to law firm clients who deploy Vertrag.AI. Pickles GmbH's responsibility as provider is to document the information and controls that enable law firm deployers to fulfil their Article 26 obligations. Pickles GmbH's own obligations as provider flow from Article 16 (see Section 2.3 above).

| Article 26 Sub-provision | Obligation | Status | Notes |
|---|---|---|---|
| Article 26(1) | Deployers must use AI systems in accordance with the instructions for use provided by the provider | Partially addressed | [ASSUMPTION] Anthropic's API terms of service and usage policies govern permitted use of the Claude model. Pickles GmbH must ensure Vertrag.AI's use case is within permitted scope. Flag for Legal Counsel to confirm. |
| Article 26(2) | Deployers must assign human oversight to a natural person with the competence, training and authority to oversee the AI system | Partially addressed | System owner role assigned (Head of Product). Competence and training requirements not yet formally documented. |
| Article 26(3) | Deployers must ensure input data is relevant and sufficiently representative | Partially addressed | Contract documents uploaded by law firm users constitute the input data. Pickles GmbH does not control input quality directly; guidance to users on appropriate use is required. |
| Article 26(4) | Where the deployer is aware the AI system presents risk, they must notify the provider | Not yet formally addressed | Incident response pathway to Anthropic not yet documented. Flag for Incident Response Playbook (L3-6.2). |
| Article 26(5) | Deployers of high-risk AI systems must conduct a fundamental rights impact assessment before deployment | Not applicable at current classification | Would apply if classification is revised to high-risk. |
| Article 26(6) | Deployers must keep logs for the period specified by the provider, minimum 6 months | Partially addressed | [ASSUMPTION] Log retention period not confirmed. Flag for CTO to confirm retention policy against this requirement. |
| Article 26(7) | Deployers that are public authorities must register in the EU database | Not applicable | Pickles GmbH is a private company |

---

### 2.5 GPAI Model — Downstream Deployer Considerations (Articles 51–55)

Vertrag.AI deploys the Claude API, which is a General Purpose AI (GPAI) model provided by Anthropic. Anthropic holds GPAI provider obligations. Pickles GmbH's obligations as a downstream deployer of a GPAI model are addressed below.

| Obligation Area | Article Reference | Assessment |
|---|---|---|
| GPAI provider obligations | Articles 53–54 | Held by Anthropic, not Pickles GmbH. Pickles GmbH should obtain and retain a copy of Anthropic's GPAI model compliance documentation (summary or transparency report) as evidence that the upstream provider obligations are being met. |
| Downstream deployer — using GPAI for specific purpose | Article 28(2) | Where a deployer uses a GPAI model for a specific purpose (here: contract review), and makes the system available to downstream users (law firms), the deployer takes on obligations proportionate to the specific use case. Pickles GmbH's Article 50 transparency obligations and Article 16 provider obligations are the primary expression of this at the product layer. |
| GPAI systemic risk | Article 55 | Applies to GPAI models with systemic risk (above the compute threshold). Pickles GmbH should confirm with Anthropic whether the deployed Claude model version is designated as a systemic risk model, and what (if any) downstream obligations this creates. [Flag for Legal Counsel / Anthropic account review.] |

---

## 3. Non-Applicable Provisions — Confirmed and Reasoned

These provisions were assessed in the risk classification walkthrough (P2-Worked-Example-Risk-Classification-v1.md) and confirmed as not applicable to Vertrag.AI at its current design and deployment context.

| Provision | Reason Not Applicable |
|---|---|
| Article 5 — Prohibited AI practices | Vertrag.AI does not employ subliminal manipulation, biometric surveillance, social scoring, or any other prohibited practice |
| Chapter III Section 2 — High-risk AI system obligations (Articles 8–15) | Vertrag.AI is classified as limited risk; Annex III high-risk categories do not apply in the current design |
| Article 49 — CE marking | CE marking applies to high-risk AI systems only |
| Article 49 — Registration in the EU database referred to in Article 71 (provider) | Registration in the EU database applies to providers of high-risk AI systems (Article 49) and certain GPAI models; Vertrag.AI is classified as limited risk and this obligation does not currently apply. Would apply if classification is revised to high-risk. |
| Article 26(5) — Fundamental rights impact assessment | Applies to deployers of high-risk AI systems only |

> **Conditional note:** If a product change increases automation level, or if legal review concludes that Annex III Category 5 or 8 applies, Vertrag.AI would become a high-risk AI system. At that point, all Chapter III Section 2 obligations would apply, including: conformity assessment (Article 43), technical documentation to Annex IV standard (Article 11), EU database registration (Article 49), and fundamental rights impact assessment (Article 26(5)). This document would require a full revision.

---

## 4. Compliance Gap Analysis

Summary of gaps identified in Section 2, with priority and ownership.

| # | Gap | Article | Priority | Owner | Action |
|---|---|---|---|---|---|
| GAP-001 | Machine-readable labelling of AI-generated text output not yet addressed | Article 50(2) | High | Head of Engineering / Head of Product | Assess technical feasibility in DOCX output; obtain legal view on scope of obligation |
| GAP-002 | Article 50(4) deployer disclosure form not legally reviewed; law firm guidance not produced | Article 50(4) | High | Legal Counsel | Review current product UI labelling against Article 50(4) requirements; confirm whether mandatory lawyer review constitutes editorial control for the safe harbour; document guidance for law firm deployers |
| GAP-003 | AI literacy training programme not confirmed | Article 4 | Medium | Head of Product / HR | Document and deliver AI literacy training for all staff interacting with Vertrag.AI; record completion |
| GAP-004 | Incident notification pathway to Anthropic not documented | Article 26(4) | Medium | Legal Counsel / Head of Engineering | Add Anthropic notification pathway to Incident Response Playbook (L3-6.2) |
| GAP-005 | Log retention period not confirmed against 6-month minimum | Article 26(6) | Medium | CTO / Head of Engineering | Confirm retention policy; update infrastructure documentation |
| GAP-006 | Human oversight competence and training requirements not formally documented | Article 26(2) | Medium | Head of Product | Document competence requirements for the system owner role; link to training records |
| GAP-007 | Anthropic GPAI compliance documentation not yet obtained | Articles 51–55 | Low | Legal Counsel | Request Anthropic's GPAI transparency documentation or model card; retain on file |
| GAP-008 | User guidance on appropriate input data not yet produced | Article 26(3) | Low | Head of Product | Produce and publish guidance for law firm users on appropriate contract document inputs |

---

## 5. Mapping to Other Governance Documents

The obligations identified in this document are addressed across the Pickles GmbH governance framework as follows.

| Obligation Area | Primary Governance Document |
|---|---|
| Transparency and output labelling | L2-4.3-Transparency-Disclosure-Framework-v1.md |
| Human oversight design | L1-3.4-Human-Oversight-Policy-v1.md |
| Technical documentation | P2-Worked-Example-Technical-Documentation-v1.md |
| Logging and traceability | L3-6.1-AI-Monitoring-Framework-v1.md |
| Incident response and provider notification | L3-6.2-Incident-Response-Playbook-v1.md |
| Model change management | L3-6.3-Model-Change-Management-Protocol-v1.md |
| Vendor and GPAI model risk | L2-5.3-Vendor-Model-Risk-Assessment-v1.md |
| DPIA and data processing | L2-5.2-DPIA-Assessment-v1.md |

---

## 6. Review and Update Triggers

This mapping should be reviewed and updated when any of the following occur:

- [ ] EU AI Office publishes updated guidance on Article 50 obligations for document-based AI output
- [ ] Product roadmap introduces automation features that reduce or remove the mandatory lawyer review gate
- [ ] Legal Counsel completes review of Annex III classification (RC-001 from risk classification document)
- [ ] Anthropic provides GPAI compliance documentation that creates new downstream obligations
- [ ] Any Annex III category is amended by delegated act under Article 7 of the EU AI Act

---

*This document is a fictional worked example produced for educational and demonstration purposes. Vertrag.AI does not exist. All regulatory analysis is illustrative and does not constitute legal advice. Professional legal review is required before any obligations mapping is relied upon operationally.*
