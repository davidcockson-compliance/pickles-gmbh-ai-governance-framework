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
| **Pickles GmbH role** | Provider of Vertrag.AI (Article 3(3)); downstream deployer of Claude API (Article 3(4)) |
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

### 2.4 Article 26 — High-Risk Deployer Obligations (Not Currently Triggered for Vertrag.AI)

Article 26 sets out obligations for deployers of high-risk AI systems, not deployers generally. Vertrag.AI is currently classified as limited risk, so Article 26 is not currently triggered for law firm clients in the present worked example. This section is retained as a forward-looking reference point in case later legal review or product change causes Vertrag.AI to be reclassified as high-risk. Pickles GmbH's current responsibility is to provide documentation, instructions for use, and governance controls that would support deployer compliance if a future high-risk classification were triggered.

| Article 26 reference | Official obligation | Applicability to Vertrag.AI | Notes |
|---|---|---|---|
| Article 26(1) | Deployers of high-risk AI systems must use the system in accordance with the provider's instructions for use | Not currently triggered | Vertrag.AI is currently classified as limited risk, so Article 26 does not currently apply. If reclassified as high-risk, law firm deployers would need clear instructions for use from Pickles GmbH. |
| Article 26(2) | Deployers of high-risk AI systems must assign human oversight to natural persons with the necessary competence, training and authority, and the necessary support | Not currently triggered | If reclassified as high-risk, law firm deployers would need formally designated human reviewers with documented competence and escalation authority. |
| Article 26(3) | Paragraphs 1 and 2 are without prejudice to other deployer obligations under Union or national law and to deployer freedom to organise resources and activities | Not currently triggered | This paragraph does not create a standalone operational control, but clarifies that Article 26 sits alongside other legal obligations. |
| Article 26(4) | To the extent the deployer controls the input data, the deployer must ensure that input data is relevant and sufficiently representative in view of the intended purpose | Not currently triggered | If high-risk classification were triggered, law firm deployers would need guidance on appropriate source-document quality and intended-purpose boundaries. |
| Article 26(5) | Deployers must monitor operation in line with the instructions for use and, where relevant, inform providers in accordance with Article 72; if they have reason to consider the system presents a risk, they must inform the provider/distributor and relevant authority and suspend use | Not currently triggered | If high-risk classification were triggered, Pickles GmbH would need a formal deployer notification pathway and suspension/escalation guidance. |
| Article 26(6) | Deployers must keep automatically generated logs, to the extent under their control, for an appropriate period of at least six months unless otherwise required by law | Not currently triggered | If high-risk classification were triggered, retention periods and log-access responsibilities would need to be specified contractually and operationally. |
| Article 26(7) | Employer-deployers must inform workers' representatives and affected workers before putting the system into service or using it at the workplace | Not currently triggered | Relevant only where the deployer is an employer using a high-risk system in the workplace. |
| Article 26(8) | Public-authority deployers must comply with Article 49 registration obligations and must not use an unregistered high-risk system | Not currently triggered | Not applicable to Pickles GmbH; would only matter for public-sector deployers using a high-risk system. |
| Article 26(9) | Deployers must use Article 13 information where applicable to comply with DPIA obligations under GDPR Article 35 / LED Article 27 | Not currently triggered | Relevant only if the system becomes high-risk and personal-data processing triggers DPIA obligations. |
| Article 26(10)–(12) | Special rules for post-remote biometric identification, Annex III decision contexts, and cooperation with authorities | Not currently triggered | Not relevant to the current Vertrag.AI use case. |

---

### 2.5 GPAI Model — Downstream Deployer Considerations (Articles 51–55)

Vertrag.AI deploys the Claude API, which is a General Purpose AI (GPAI) model provided by Anthropic. Anthropic holds GPAI provider obligations. Pickles GmbH's obligations as a downstream deployer of a GPAI model are addressed below.

| Obligation Area | Article Reference | Assessment |
|---|---|---|
| GPAI provider obligations | Articles 53–54 | Held by Anthropic, not Pickles GmbH. Pickles GmbH should obtain and retain a copy of Anthropic's GPAI model compliance documentation (summary or transparency report) as evidence that the upstream provider obligations are being met. |
| Downstream integration of an upstream GPAI model | Article 3 definitions; Article 53(1)(b) | Pickles GmbH integrates an upstream GPAI model into a downstream AI system made available under its own name. At the product layer, Pickles GmbH is the provider of Vertrag.AI and must assess its own obligations by reference to the characteristics and risk classification of the downstream system. As an upstream GPAI provider, Anthropic must provide sufficient technical documentation and information to enable downstream providers to understand the capabilities and limitations of the model and support compliance at the integrated-system layer. |
| GPAI systemic risk | Article 55 | Applies to GPAI models with systemic risk (above the compute threshold). Pickles GmbH should confirm with Anthropic whether the deployed Claude model version is designated as a systemic risk model, and what (if any) downstream obligations this creates. [Flag for Legal Counsel / Anthropic account review.] |

---

## 3. Non-Applicable Provisions — Confirmed and Reasoned

These provisions were assessed in the risk classification walkthrough (P2-Worked-Example-Risk-Classification-v1.md) and confirmed as not applicable to Vertrag.AI at its current design and deployment context.

| Provision | Reason Not Applicable |
|---|---|
| Article 5 — Prohibited AI practices | Vertrag.AI does not employ subliminal manipulation, biometric surveillance, social scoring, or any other prohibited practice |
| Chapter III Section 2 — High-risk AI system obligations (Articles 8–15) | Vertrag.AI is classified as limited risk; Annex III high-risk categories do not apply in the current design |
| Article 48 — CE marking | CE marking applies to high-risk AI systems only |
| Article 49 — Registration in the EU database referred to in Article 71 (provider) | Registration in the EU database applies to providers of high-risk AI systems (Article 49) and certain GPAI models; Vertrag.AI is classified as limited risk and this obligation does not currently apply. Would apply if classification is revised to high-risk. |
| Article 27 — Fundamental rights impact assessment | Applies only to specified deployers of certain high-risk AI systems (including bodies governed by public law, private entities providing public services, and deployers of certain Annex III point 5 systems). Vertrag.AI is currently classified as limited risk, so Article 27 is not currently triggered. |

> **Conditional note:** If a product change increases automation level, or if legal review concludes that Annex III Category 5 or 8 applies, Vertrag.AI would become a high-risk AI system. At that point, all Chapter III Section 2 obligations would apply, including: conformity assessment (Article 43), technical documentation to Annex IV standard (Article 11), EU database registration (Article 49), and where the deployer falls within the categories covered by Article 27, a fundamental rights impact assessment. This document would require a full revision.

---

## 4. Compliance Gap Analysis

Summary of gaps identified in Section 2, with priority and ownership.

| # | Gap | Article | Priority | Owner | Action |
|---|---|---|---|---|---|
| GAP-001 | Machine-readable labelling of AI-generated text output not yet addressed | Article 50(2) | High | Head of Engineering / Head of Product | Assess technical feasibility in DOCX output; obtain legal view on scope of obligation |
| GAP-002 | Article 50(4) deployer disclosure form not legally reviewed; law firm guidance not produced | Article 50(4) | High | Legal Counsel | Review current product UI labelling against Article 50(4) requirements; confirm whether mandatory lawyer review constitutes editorial control for the safe harbour; document guidance for law firm deployers |
| GAP-003 | AI literacy training programme not confirmed | Article 4 | Medium | Head of Product / HR | Document and deliver AI literacy training for all staff interacting with Vertrag.AI; record completion |
| GAP-004 | Incident notification pathway to Anthropic not documented | Article 26(5) (forward-looking — not currently triggered; Article 26 applies to high-risk AI systems only) | Medium | Legal Counsel / Head of Engineering | Add Anthropic notification pathway to Incident Response Playbook (L3-6.2); note this becomes mandatory if Vertrag.AI is reclassified as high-risk |
| GAP-005 | Log retention period not confirmed against 6-month minimum | Article 26(6) | Medium | CTO / Head of Engineering | Confirm retention policy; update infrastructure documentation |
| GAP-006 | Human oversight competence and training requirements not formally documented | Article 26(2) | Medium | Head of Product | Document competence requirements for the system owner role; link to training records |
| GAP-007 | Anthropic GPAI compliance documentation not yet obtained | Articles 51–55 | Low | Legal Counsel | Request Anthropic's GPAI transparency documentation or model card; retain on file |
| GAP-008 | User guidance on appropriate input data not yet produced | Article 26(4) (forward-looking — not currently triggered; Article 26 applies to high-risk AI systems only) | Low | Head of Product | Produce and publish guidance for law firm users on appropriate contract document inputs; note this becomes mandatory for high-risk deployers if Vertrag.AI is reclassified |

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
