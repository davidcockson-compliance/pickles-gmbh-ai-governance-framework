# Regulatory Orientation Note — Stage 1
**Project:** Pickles GmbH — AI Governance Framework
**Stage:** Stage 1 — Regulatory Orientation
**Status:** Draft
**Version:** v1
**Date:** 2026-02-22
**Assumptions:** Built on outline assumptions — not verified against real Pickles GmbH data

---

## Purpose of This Document

This note establishes the regulatory landscape applicable to Pickles GmbH [ASSUMPTION — A-003] as a provider of legal AI tools to German legal professionals. It extracts the obligations that the AI Governance & Operational Architecture Framework must address, drawn directly from the source documents in `_input/`. It does not interpret or supplement those documents beyond what is stated in them.

All provisions cited are traceable to source documents in `_input/`. Where a provision cannot be confirmed in source documents, it is flagged as [UNVERIFIED].

---

## 1. EU AI Act: Classification of Legal AI Systems

**Source:** Regulation (EU) 2024/1689 of 13 June 2024 (EU AI Act), as read from `_input/EU-AI-Act-full-text.pdf`

### 1.1 Risk Classification Framework

The EU AI Act establishes a risk-based hierarchy with four tiers:

| Tier | Status | Consequence |
|------|--------|-------------|
| Prohibited AI | Article 5 | Cannot be placed on market. Examples: real-time biometric identification for law enforcement in public spaces; social scoring; manipulation techniques. |
| High-Risk AI | Articles 6 + Annex III | Mandatory pre-market requirements: documentation, conformity assessment, human oversight, logging. |
| Limited-Risk AI | Article 50 | Transparency obligations only — disclosure when interacting with natural persons. |
| Minimal Risk | General | Voluntary self-regulation only. |

### 1.2 Classification of Legal AI Systems

The EU AI Act explicitly addresses AI in legal and judicial contexts.

**Recital 61** identifies AI systems intended for use by judicial authorities (or on their behalf) for:
- Assisting with fact-finding
- Legal research
- Prediction of legal outcomes applied to **a concrete set of facts**

...as **high-risk** when their outputs are used in the administration of law.

**Exception:** Systems performing ancillary administrative functions (pseudonymisation, document management) are **not** classified as high-risk under Recital 61.

**Application to Pickles GmbH** [ASSUMPTION — A-001]:

| Use Case | Likely Classification | Rationale |
|----------|----------------------|-----------|
| Legal drafting assistance | Unclear | Ancillary if tool only suggests; potentially high-risk if applied to specific facts to produce binding drafts |
| Legal research assistance | Likely ancillary / lower risk | Research support without autonomous conclusions |
| Summarisation | Likely ancillary / lower risk | Unless summaries applied to specific facts in decision-making |
| Legal analysis applied to specific client facts | Likely **high-risk** | AI analysis applied to specific facts — Recital 61 |

> [LEGAL REVIEW REQUIRED] The boundary between ancillary and high-risk for legal AI tools depends on actual deployment context. A qualified lawyer must review the application of Recital 61 and Annex III to Pickles GmbH's specific product capabilities before the risk classification is finalised.

**Key classification principle (Recital 53):** An AI system "does not necessarily influence the outcome of decision-making should be understood to be an AI system that does not have an impact on the substance, and therefore the outcome, of decision-making."

### 1.3 Key Obligations for High-Risk AI System Providers

Where Pickles GmbH's systems are classified as high-risk, the following obligations apply:

**Technical Documentation (Article 11):**
- System description and intended purpose
- Data and development methodology
- Training, validation, and testing methodology
- Performance assessment and known limitations
- Human oversight design
- Logging and automatic recording capabilities

**Risk Management (Article 9):**
- Continuous, iterative risk management process across the full system lifecycle
- Identify and document foreseeable misuse scenarios
- Identify risks of errors, bias, and discrimination
- Implement and document risk mitigation measures
- Review and update regularly

**Data Quality and Governance (Article 10):**
- Training, validation, and test data must be relevant, representative, free of errors, and complete
- Statistical properties must be appropriate for the system's intended use
- Data must be assessed for bias and potential for discriminatory outcomes
- Data minimisation required

**Human Oversight (Article 14):**
- High-risk systems must be designed to allow human override at all times
- Human reviewers must have the competence, training, and authority to intervene
- Fully automated legal decisions without human review are incompatible with high-risk classification requirements
- Recital 91: Deployers must ensure humans overseeing high-risk systems are competent to do so

**Transparency and Information (Article 13):**
- Instructions for use must be clear, comprehensive, and accessible
- Characteristics, capabilities, and limitations must be documented for deployers

**Logging and Traceability (Article 12):**
- High-risk systems must automatically record events throughout their operational lifetime

**Quality Management and Post-Market Monitoring (Articles 17 and 72):**
- Providers must maintain a sound quality management system
- Post-market monitoring must track system performance throughout its lifecycle and report serious incidents to market surveillance authorities

### 1.4 Transparency Obligations — AI Systems Interacting with Humans (Article 50)

Even where an AI system is not classified as high-risk, Article 50 requires:
- Users must be informed they are interacting with an AI system
- Clear disclosure of circumstances and context of use
- Where AI generates synthetic text, users must be clearly informed the content is AI-generated (exceptions: satirical, artistic, or analogous work with appropriate safeguards; and where content has been subject to human review and editorial responsibility — Recital 132-133)

[ASSUMPTION — A-006] It is assumed that Pickles GmbH's products include interfaces through which legal professionals interact directly with the AI system. This assumption must be verified before Article 50 obligations are mapped to specific product features.

**EU AI Act Article 50 (effective 2 August 2026):** Providers of AI systems interacting with natural persons (e.g., legal chatbots) must:
- Inform users they are interacting with AI (Article 50(1))
- Label AI-generated content as AI-generated (Article 50(2), (5))

### 1.5 Conformity Assessment Requirements (Articles 16-23)

For high-risk AI systems, providers must:
- Perform conformity assessment before market placement
- Maintain all required documentation
- Draw up a Declaration of Conformity
- Affix CE marking
- Establish and maintain a quality management system

**Conformity assessment procedures (Articles 43(1) and 43(2)):** For high-risk AI systems listed in Annex III point 1, or where applicable harmonised standards are absent, conformity assessment requires involvement of a notified body (Article 43(1)). For high-risk AI systems listed in Annex III points 2–8, the conformity assessment procedure is based on **internal control**, which does not require the involvement of a notified body (Article 43(2)). [LEGAL REVIEW REQUIRED — the applicable procedure depends on the specific Annex III classification of each system]

**Substantial modification (Article 3):** Changes that affect compliance with high-risk requirements require a new conformity assessment. Providers must track all changes that could constitute a substantial modification.

### 1.6 AI Competence Obligation (Article 4 — Effective 2 February 2025)

Providers and operators must take measures to ensure staff involved in the operation and use of AI systems have **sufficient AI competence**, taking into account technical knowledge, experience, education, and training in context. This obligation has been in force since 2 February 2025.

---

## 2. GDPR: Key Obligations for a Legal AI Provider

**Source:** Regulation (EU) 2016/679 (GDPR), as read from `_input/GDPR-full-text.pdf`

### 2.1 Processing Principles (Article 5)

All personal data processing by Pickles GmbH must comply with Article 5:

| Principle | Requirement |
|-----------|------------|
| Lawfulness, fairness, transparency | Processing must have a valid legal basis (Article 6); data subjects must be informed |
| Purpose limitation | Data collected for specified, explicit, legitimate purposes; not further processed incompatibly |
| Data minimisation | Only data adequate, relevant, and limited to what is necessary |
| Accuracy | Data must be accurate; inaccurate data erased or rectified without delay |
| Storage limitation | Kept no longer than necessary for the purpose |
| Integrity and confidentiality | Appropriate security against unauthorised access, loss, destruction, or damage |
| Accountability | Controller must be able to demonstrate compliance with all of the above |

**Lawful bases for processing (Article 6):** One of the following must apply: (a) consent; (b) contract; (c) legal obligation; (d) vital interests; (e) public task; (f) legitimate interests.

### 2.2 Article 28 — Processor Obligations

[ASSUMPTION — A-007] It is assumed that Pickles GmbH will act as a **data processor** on behalf of its lawyer clients (the **data controllers**) when processing personal data contained in legal documents. This structural assumption is fundamental to the governance framework and must be verified.

> [LEGAL REVIEW REQUIRED] Whether Pickles GmbH acts as a processor, joint controller, or independent controller for specific processing activities must be assessed by a qualified lawyer. This determines the structure of all client contracts and the legal basis for processing.

If Pickles GmbH is a processor, Article 28 requires:

**Controller selection duty (Article 28(1)):** Controllers may only use processors that provide **sufficient guarantees** to implement appropriate technical and organisational measures ensuring GDPR compliance.

**Processor obligations (Article 28(3)):** Processing must be governed by a written contract (the Data Processing Agreement — DPA) stipulating that Pickles GmbH as processor shall:

- (a) Process personal data only on documented instructions from the controller, including with regard to international transfers
- (b) Ensure persons authorised to process personal data are bound by confidentiality
- (c) Take all security measures required by Article 32
- (d) Respect conditions for engaging sub-processors (Article 28(2) — prior specific or general written authorisation from the controller; sub-processors subject to same obligations by contract)
- (e) Assist the controller in responding to data subject rights requests (Articles 15-22)
- (f) Assist the controller in obligations under Articles 32-36 (security, breach notification, DPIA, prior consultation)
- (g) Delete or return all personal data at the end of services; delete existing copies unless Union or Member State law requires otherwise
- (h) Make available all information necessary to demonstrate compliance; allow for and contribute to audits, including inspections, conducted by the controller or auditor mandated by the controller
- Notify the controller immediately if any instruction infringes GDPR (Article 28(3), final paragraph)

**DPA form (Article 28(9)):** The contract must be in writing, including in electronic form.

**Sub-processor liability (Article 28(4)):** Where Pickles GmbH engages a sub-processor (e.g., a third-party AI model provider), the same data protection obligations must be imposed by contract. Pickles GmbH remains fully liable to the controller for the sub-processor's performance.

**Standard Contractual Clauses (Article 28(6)-(8)):** DPAs may be based on Commission or supervisory authority-approved SCCs.

### 2.3 Chapter III — Rights of Data Subjects (Articles 12-23)

Where Pickles GmbH processes personal data of individuals named in legal documents, the following rights must be supported:

| Article | Right | Key Content |
|---------|-------|------------|
| Art. 12 | Modalities | Respond concisely, transparently, intelligibly; free of charge; within 1 month (extendable by 2 months for complexity) |
| Art. 13 | Information (data from subject) | At point of collection: controller identity, DPO contact, purposes, legal basis, recipients, retention, rights, and existence of automated decision-making (Art. 13(2)(f)) |
| Art. 14 | Information (data not from subject) | Within 1 month: same information plus source of data. Exception: Art. 14(5)(d) — does not apply where professional secrecy obligation applies under Union or Member State law |
| Art. 15 | Access | Right to confirmation of processing and copy of personal data |
| Art. 16 | Rectification | Right to correction of inaccurate data without undue delay |
| Art. 17 | Erasure | Right to deletion where: no longer necessary; consent withdrawn; objection upheld; unlawful processing; legal obligation to erase. Exceptions: freedom of expression; legal obligation; legal claims (Art. 17(3)) |
| Art. 18 | Restriction | Right to restrict processing where accuracy contested; processing unlawful and data subject opposes erasure; data needed for legal claims; objection pending |
| Art. 19 | Notification | Controller must notify each recipient of rectification, erasure, or restriction; inform data subject of recipients on request |
| Art. 20 | Portability | Right to receive data in structured, machine-readable format where basis is consent or contract and processing is automated |
| Art. 21 | Right to object | Right to object to processing based on legitimate interests (Art. 6(1)(f)); absolute right to object to direct marketing including profiling |
| Art. 22 | Automated decision-making | See Section 2.4 below |
| Art. 23 | Restrictions | Member States may restrict these rights by law for specified purposes (national security, defence, criminal proceedings, etc.) |

**Professional secrecy note:** Article 14(5)(d) provides that the obligation to provide information under Article 14 does not apply where personal data must remain confidential subject to an obligation of professional secrecy regulated by Union or Member State law. This is directly relevant in the legal context, where lawyer-client confidentiality may restrict transparency obligations.

### 2.4 Article 22 — Automated Individual Decision-Making, Including Profiling

**Core right (Article 22(1)):** Data subjects have the right not to be subject to a decision based **solely** on automated processing — including profiling — which produces **legal effects** concerning them or **similarly significantly affects** them.

**Exceptions (Article 22(2)):** The right does not apply where the decision:
- (a) Is necessary for entering into or performance of a contract
- (b) Is authorised by Union or Member State law with appropriate safeguards
- (c) Is based on the data subject's explicit consent

**Safeguards mandatory in exceptions (a) and (c) (Article 22(3)):**
- Right to obtain human intervention on the part of the controller
- Right to express the data subject's point of view
- Right to contest the decision

**Special categories prohibition (Article 22(4)):** Automated decisions must not be based on special categories of data (Article 9(1)) unless Article 9(2)(a) or (g) applies and suitable safeguards are in place.

**Application to legal AI** [ASSUMPTION — A-001, A-007]: If Pickles GmbH's systems generate analysis or recommendations that are adopted without human review to produce decisions with legal effects on individuals, Article 22 is triggered. This reinforces the human oversight obligation under EU AI Act Article 14 and BRAK professional conduct rules.

### 2.5 Article 25 — Data Protection by Design and by Default

**By design (Article 25(1)):** At the time of determining the means of processing and at the time of processing itself, controllers must implement appropriate technical and organisational measures — such as pseudonymisation — to implement data protection principles effectively and integrate necessary safeguards.

**By default (Article 25(2)):** By default, only personal data **necessary** for each specific purpose must be processed. This obligation applies to amount of data collected, extent of processing, storage period, and accessibility.

### 2.6 Article 32 — Security of Processing

Controllers and processors must implement appropriate technical and organisational measures ensuring security appropriate to the risk, including as appropriate:

- (a) Pseudonymisation and encryption of personal data
- (b) Ability to ensure ongoing confidentiality, integrity, availability, and **resilience** of processing systems and services
- (c) Ability to restore availability and access to personal data in a timely manner in the event of a physical or technical incident
- (d) A process for regularly testing, assessing, and evaluating the effectiveness of technical and organisational security measures

**Risk assessment basis (Article 32(2)):** Security risk includes accidental or unlawful destruction, loss, alteration, unauthorised disclosure of, or access to personal data transmitted, stored, or otherwise processed.

**Staff access controls (Article 32(4)):** Any person acting under the authority of the controller or processor with access to personal data must not process them except on instructions from the controller.

### 2.7 Article 35 — Data Protection Impact Assessment

**Trigger (Article 35(1)):** Where a type of processing — particularly using new technologies — is likely to result in a **high risk** to the rights and freedoms of natural persons, a DPIA must be carried out **prior to processing**. A single assessment may address a set of similar processing operations presenting similar high risks.

**Mandatory DPIA triggers (Article 35(3)):**
- (a) Systematic and extensive evaluation of personal aspects based on automated processing, including profiling, on which decisions producing legal effects or similarly significantly affecting persons are made
- (b) Processing on a large scale of special categories of data (Article 9(1)) or personal data relating to criminal convictions (Article 10)
- (c) Systematic monitoring of a publicly accessible area on a large scale

[ASSUMPTION — A-001, A-007] Pickles GmbH's systems likely trigger Article 35(3)(a) if they perform automated analysis of personal data to produce legal analysis or recommendations, and Article 35(3)(b) if they process special categories of data within legal documents. A DPIA is therefore likely mandatory before deployment of any legal AI system that processes personal data.

**DPIA must contain at minimum (Article 35(7)):**
- (a) Systematic description of envisaged processing operations and purposes, including the legitimate interest pursued by the controller where applicable
- (b) Assessment of the necessity and proportionality of the processing operations in relation to the purposes
- (c) Assessment of the risks to the rights and freedoms of data subjects
- (d) Measures envisaged to address the risks, including safeguards, security measures, and mechanisms to ensure protection of personal data and demonstrate compliance

**DPO involvement (Article 35(2)):** The controller must seek the advice of the DPO when carrying out a DPIA.

**Review requirement (Article 35(11)):** Controller must carry out a review at least when there is a change in the risk represented by processing operations.

**Prior consultation (Article 36):** Where a DPIA indicates that processing would result in high risk in the absence of mitigation measures, the controller must consult the supervisory authority **prior to processing**. The supervisory authority has up to eight weeks (extendable by six weeks for complex cases) to provide written advice. Consultation is required with the following information: responsibilities of all parties; purposes and means of intended processing; measures and safeguards to protect data subjects; DPO contact details; and the DPIA itself.

### 2.8 International Data Transfers (Articles 44-49)

**General principle (Article 44):** All transfers of personal data to third countries or international organisations may take place only if Chapter V conditions are complied with — including onward transfers.

[ASSUMPTION — A-004, A-005] If Pickles GmbH uses third-party AI model providers based outside the EU/EEA, or if data is processed on servers outside the EU/EEA, these transfer provisions apply.

**Transfer mechanisms in order of preference:**

| Mechanism | Article | Notes |
|-----------|---------|-------|
| Adequacy decision | Art. 45 | Commission decision that third country ensures adequate protection — no further authorisation required |
| Standard Contractual Clauses (SCCs) | Art. 46(2)(c)-(d) | Commission or supervisory authority-approved SCCs — no further authorisation required |
| Binding Corporate Rules (BCRs) | Art. 47 | For intra-group transfers within a corporate group |
| Approved code of conduct + binding commitments | Art. 46(2)(e) | |
| Approved certification mechanism + binding commitments | Art. 46(2)(f) | |
| Derogations | Art. 49 | Exceptions only: consent, contract performance, important public interest, legal claims, vital interests |

**Key risk for US-based AI providers:** The EU-US Data Privacy Framework provides a current adequacy mechanism for certified US organisations. Providers not certified under this framework require SCCs.

---

## 3. BDSG: German Law Overlay on GDPR

**Source:** BDSG (German Federal Data Protection Act), as read from `_input/BDSG-German-Federal-Data-Protection-Act-EN.pdf`

### 3.1 Application

**Sections 1(4) and 1(7) BDSG:** BDSG applies to controllers and processors processing personal data in Germany or in the context of a German establishment. Where GDPR applies directly, BDSG provisions apply only where GDPR does not conclusively govern the matter. BDSG fills gaps and provides German-specific implementation.

**Section 2 BDSG:** Pickles GmbH as a private legal entity is a "private body" for BDSG purposes.

### 3.2 Mandatory DPO Designation (Section 38 BDSG)

**Section 38(1) BDSG:** A DPO must be designated if the controller or processor **consistently employs at least 20 persons** dealing with automated processing of personal data. This threshold is lower than GDPR Article 37, which focuses on large-scale or systematic monitoring.

Additionally, Section 38(1) BDSG requires a DPO where the controller undertakes processing subject to DPIA under GDPR Article 35, regardless of staff count.

[ASSUMPTION — A-008] Whether Pickles GmbH meets the 20-person threshold is unverified. If it does, DPO designation is mandatory under BDSG Section 38.

**DPO tasks (Section 7 BDSG):** In addition to GDPR tasks, the DPO must monitor compliance with both GDPR and BDSG provisions and advise on DPIAs under Section 67 BDSG.

### 3.3 Automated Decision-Making — BDSG Overlay

**Section 37 BDSG:** The GDPR Article 22(1) right not to be subject to automated decisions does not apply in the context of certain insurance contract services.

**Section 54 BDSG (law enforcement context):** Decisions based solely on automated processing producing adverse legal effects shall be permitted only if authorised by law. Profiling resulting in discrimination against natural persons is **prohibited**.

### 3.4 Data Subject Rights — Professional Confidentiality Modifications

**Section 29 BDSG:** The right of access (GDPR Article 15) and transparency obligations (GDPR Article 14) do not apply where disclosure would breach the legitimate interests of a third party, including professional confidentiality obligations. This directly reinforces the Anwaltgeheimnis (attorney-client privilege) requirements described in Section 5 below.

### 3.5 DPIA and Prior Consultation with BfDI

**Section 67 BDSG:** Where processing using new technologies is likely to result in a substantial risk to the legally protected interests of data subjects, a DPIA is mandatory prior to processing. This applies independently of the GDPR Article 35 trigger.

**Section 69 BDSG:** Prior consultation with the BfDI (Federal Commissioner for Data Protection and Freedom of Information) is required before processing commences if:
- DPIA indicates substantial risk that the controller cannot sufficiently mitigate; or
- Processing using new technologies or mechanisms involves substantial risk to legally protected interests

**BfDI response time (Section 69(3) BDSG):** The BfDI has up to **six weeks** to provide written advice (extendable by one month for especially complex processing). If processing is especially urgent, it may commence after consultation begins but before the period expires — BfDI recommendations must then be applied retroactively (Section 69(4)).

> [LEGAL REVIEW REQUIRED] This prior consultation obligation applies to all new legal AI systems deployed by Pickles GmbH that involve substantial risk. The BfDI consultation process should be initiated at the design stage, not after deployment.

### 3.6 Technical and Organisational Security Controls (Section 64 BDSG)

Section 64 BDSG requires the following specific controls for automated processing systems:

| Control Type | Requirement |
|-------------|------------|
| Equipment access control | Deny unauthorised persons access to processing equipment |
| Data media control | Prevent unauthorised reading, copying, modification, or erasure of data media |
| Storage control | Prevent unauthorised input, inspection, modification, or deletion of stored personal data |
| User control | Prevent use of automated processing systems by unauthorised persons |
| Data access control | Ensure authorised users access only personal data covered by their authorisation |
| Input control | Verify and establish who input personal data, and when |
| Transport control | Ensure confidentiality and integrity during transfer of personal data |
| Recovery | Ensure installed systems can be restored in case of interruption |
| Reliability | Ensure all system functions perform and faults are reported |
| Integrity | Ensure stored personal data cannot be corrupted by system malfunction |
| Processing control | Ensure personal data processed on behalf of controller is processed only per controller instructions |
| Availability control | Ensure personal data is protected against loss and destruction |
| Separability | Ensure personal data collected for different purposes can be processed separately |

### 3.7 Mandatory Audit Logging (Section 76 BDSG)

Controllers and processors must provide logs for at minimum the following operations in automated processing systems:
1. Collection
2. Alteration
3. Consultation
4. Disclosure (including transfers)
5. Combination
6. Erasure

Logs of consultation and disclosure must record: justification; date and time; and, as far as possible, the identity of the person consulting or disclosing data and the identity of recipients.

**Permitted uses (Section 76 BDSG):** Logs may only be used by the DPO, BfDI, or data subject to verify lawfulness of processing.

**Retention:** Log data must be erased at the end of the year following the year in which they were generated.

### 3.8 Enforcement and Penalties

**Section 42 BDSG:** Deliberate, unauthorised transfer of personal data of large numbers of people for commercial purposes — **up to three years' imprisonment** or a fine.

**Section 43 BDSG:** Administrative fines of up to **€50,000** for specific BDSG violations. These are in addition to GDPR Article 83 fines (up to €20 million or 4% of global annual turnover for GDPR violations).

**Section 83 BDSG:** Compensation liability for data subjects where personal data is processed in violation of BDSG or applicable law.

**Supervisory authority (Sections 8-9, 40 BDSG):** BfDI supervises federal public bodies and certain private bodies. The Landesbehörden (state data protection authorities) supervise private bodies. If Pickles GmbH is headquartered in Germany, the competent Landesbehörde is the primary supervisory authority for GDPR purposes (one-stop-shop mechanism).

---

## 4. EDPB Guidelines 05/2020 — Consent Under GDPR

**Source:** EDPB Guidelines 05/2020 on Consent under Regulation 2016/679 (v1.1, adopted 4 May 2020), as read from `_input/EDPB-Guidelines-05-2020-consent.pdf`

**Scope clarification:** These Guidelines address **consent as a lawful basis for data processing** under GDPR Article 4(11) and Article 7. They are **not** guidance on automated decision-making. The project specification references "EDPB Guidelines 05/2020 implications for automated decision-making in legal context" — however, the document in `_input/` is exclusively about consent. The dedicated guidelines on automated decision-making are WP29 Guidelines on Automated Decision-Making and Profiling (WP251 rev.01, October 2017), which are referenced within Guidelines 05/2020 (Paragraph 92) but were **not included in `_input/`**. [UNVERIFIED — WP251 provisions not confirmed from source documents.]

The following consent provisions are relevant to Pickles GmbH.

### 4.1 Requirements for Valid Consent

Where Pickles GmbH or its lawyer clients rely on **consent** as a lawful basis for any processing, consent must meet all four requirements:

**Freely given (Paragraphs 13-24):**
- Real choice and control for the data subject
- Power imbalances create a presumption that consent is not freely given (Para. 16)
- Consent bundled with service terms is presumptively invalid unless separate consent is also offered (Para. 26-31)

**Specific (Paragraphs 55-61):**
- Must relate to one or more specific, identified purposes
- Separate consent required for each distinct purpose; granularity is required (Para. 42-45)
- Purpose must be described in clear, plain language — not technical jargon (Para. 56)

**Informed (Paragraphs 62-74):**
Minimum information required at the point of consent (Paragraph 64):
- (i) Identity of the controller
- (ii) Purpose of each processing operation
- (iii) Types of data collected and used
- (iv) Right to withdraw consent
- **(v) Information about the use of data for automated decision-making, including profiling, in accordance with Article 22(2)(c) — where relevant**
- (vi) Risks of data transfers to third countries due to absence of adequacy decision or safeguards

**Unambiguous (Paragraphs 75-90):**
- Must be by a statement or clear affirmative action (Para. 76)
- Pre-ticked opt-in boxes = **not valid** consent (Para. 81)
- Silence, inactivity, scrolling, or swiping = **not valid** consent (Para. 86)
- Consent must be given **before** processing begins (Para. 90)

### 4.2 Demonstrating and Managing Consent

**Demonstrability (Article 7(1); Paragraphs 104-111):** Controllers must **prove** that valid consent was obtained. Documentary records of consent statements and the consent workflow must be maintained. Records must be linked to the specific processing activity.

**Withdrawal (Article 7(3); Paragraphs 112-120):** Consent must be withdrawable **as easily as it was given**. Withdrawal does not affect the lawfulness of prior processing. If processing is to continue after withdrawal, another lawful basis must be identified in advance.

**Lawful basis switching (Paragraphs 121-123):** Controllers **cannot switch** from consent to another lawful basis after consent is withdrawn.

### 4.3 Implications for Legal AI

- If consent is used as the lawful basis for any AI processing, all of the above standards must be met
- Disclosure of automated decision-making (Para. 64(v)) is mandatory in consent notices where processing involves Article 22 profiling or automated decisions
- GDPR Article 5 data protection principles apply even where consent is validly obtained

---

## 5. BRAK Position Paper — AI in Legal Practice

**Source:** BRAK, "Notes on the Use of Artificial Intelligence in Legal Practice" (December 2024), as read from `_input/BRAK-AI-position-paper en-GB.pdf`

### 5.1 BRAK's Overall Position

BRAK acknowledges efficiency gains from legal AI tools but establishes that "the use of AI does not release lawyers from their duty to provide legal advice to clients and represent their interests independently and on their own responsibility."

**Core principle:** "AI systems should only be used to support a solicitor's work and must not replace it." (BRAK Position Paper, Section 2.1)

These obligations bind **lawyers using** Pickles GmbH's tools. As the tool provider, Pickles GmbH must design its systems to support — not undermine — compliance with these obligations.

### 5.2 Professional Duty Obligations

**Mandatory independent review (Section 2.1; Section 43(1) BRAO):**
"In any case, independent review and final inspection of AI results by the solicitor is required." This applies to all AI outputs: drafting, research, analysis, and summarisation. [ASSUMPTION — A-001]

**No replacement of lawyer judgment (Section 2.1):**
AI systems must support the lawyer's professional judgment. Systems that imply legal review is unnecessary are non-compliant with professional conduct rules.

**Heightened duty of care for client-facing use (Section 2.2):**
Where AI is used in client-facing interactions — chatbots, auto-responders, client intake automation — "a higher standard of due diligence applies." It "must not be implied that legal review and advice are not necessary in individual cases."

**No mandatory obligation to use AI (Section 2.3):**
BRAO and BORA do not currently require lawyers to use AI tools, though the law firm obligation under Section 5 BORA (maintaining necessary organisational resources) may require AI use for mass proceedings.

### 5.3 Attorney-Client Privilege — Anwaltgeheimnis

**Legal basis (Section 43a(2) BRAO):**
Attorney-client privilege covers **all** information obtained in the course of a mandate, including client identity and the fact that a mandate has been granted. Post-mandate obligations continue under Section 2(1) BORA. Unauthorised disclosure is a criminal offence under Section 203(1)(3) StGB.

**Scope:** "Since, in principle, 'everything' from a mandate is covered, the names of clients and the fact that a mandate has been granted at all are also covered by the duty of confidentiality." (Section 3, BRAK Position Paper)

**Practical obligations for legal AI use (Sections 3.1-3.2):**
- Only abstract prompts that do not allow identification of a specific mandate should be used where possible
- Documents uploaded must be fully anonymised before upload where possible
- Removing names and addresses alone is **insufficient** if client identity can be inferred from context

**Criminal liability threshold (Section 3.2):**
"For the offence of accessing client secrets, it is irrelevant whether the AI providers actually take note of the information. It is sufficient that they have the opportunity to do so."

> [LEGAL REVIEW REQUIRED] This threshold creates significant risk for any legal AI product that receives unredacted client data, even if that data is not stored or accessed by the provider. Legal advice is required on the design of data handling and anonymisation workflows.

### 5.4 IT Outsourcing Requirements — Section 43e BRAO

**Need-to-know principle:** Lawyers may only grant AI providers access to confidential information where **strictly necessary** for the service. Unnecessary access violates Section 43e BRAO.

**Written service agreements (Sections 43e(2) and (3) BRAO — mandatory minimum content):**
- Obligation to maintain confidentiality, with explicit warning of criminal consequences for breach
- Obligation to adhere to the purpose limitation principle

**Termination obligation:** If these standards are not (or no longer) guaranteed, the cooperation must be terminated immediately (Section 43e(2)).

**Foreign providers (Section 43e(4) BRAO):**
Where AI providers are established outside Germany, confidentiality protection must be comparable to German standards. US-based providers require specific assessment against current adequacy frameworks. Providers in countries without equivalent data protection standards (cited examples: China, India) require Standard Contractual Clauses or equivalent protective measures.

[ASSUMPTION — A-004] This provision is directly relevant if Pickles GmbH uses third-party foundation model providers. Pickles GmbH's ability to offer legally compliant service agreements to lawyer clients depends on the provenance and contractual arrangements of any underlying AI models in use.

### 5.5 Transparency and AI Output Labelling

**Current position (December 2024):** No mandatory professional obligation under BRAO or BORA to inform clients about AI use. However, transparency obligations may arise from contract law or the Unfair Competition Act (UWG).

**Best practice recommendation (Section 4):** "It is advisable to use AI tools transparently and, in case of doubt, to include a contractual provision with clients."

**EU AI Act transparency obligations for operators (Article 50 — effective 2 August 2026):**
- Lawyers as operators must disclose where AI-generated text is published to inform the public about matters of public interest
- **Safe harbour:** No disclosure obligation "if the content generated by AI has been subject to human review or editorial control and if a natural or legal person is editorially responsible for the publication"

**Pickles GmbH as provider (Article 50(1), (2), (5)):**
- Must inform users that they are interacting with AI (applicable to legal chatbots)
- Must label AI-generated content so users know it is machine-generated

### 5.6 Liability Framework

**Lawyers retain full professional liability** for all AI-generated outputs they rely on. They cannot delegate responsibility to Pickles GmbH or to any underlying AI model provider.

**Additional risk areas for lawyers using AI (Section 6):**
- **Tax law:** Above a certain degree of automation, legal activity may be reclassified as commercial activity, affecting tax status
- **Insurance:** Professional liability insurance may refuse coverage if AI use falls outside scope of "legal activity"
- **Copyright:** AI-generated text is not protected by copyright but may infringe third-party copyrights — the lawyer using the tool bears this liability

### 5.7 Regulatory Coexistence

"The use of an AI system that complies with the AI Regulation may nevertheless violate professional regulations. Conversely, a violation of certain provisions of the AI Regulation, such as Art. 4 (AI competence) or Art. 50 (transparency), may also be relevant under professional law." (Section 5.4, BRAK Position Paper)

**Compliance with the EU AI Act does not ensure BRAK compliance.** The governance framework must address both independently.

### 5.8 Ongoing Monitoring

"As the professional law discussion on the use of AI tools is highly dynamic, these notes are only a snapshot." (Section 8, BRAK Position Paper)

The governance framework must include a mechanism for monitoring BRAK guidance updates, as further notes from BRAK are expected.

---

## 6. ISO/IEC 42001 — AI Management System Standard

**Source:** ISO/IEC 42001 Overview Summary, as read from `_input/ISO-42001-overview-summary.pdf`

### 6.1 Scope

ISO/IEC 42001 is a sector-specific AI management system standard specifying requirements for organisations providing or using AI systems to **establish, implement, maintain, and continually improve** an AI Management System (AIMS) for responsible AI. It follows the ISO High-Level Structure (HLS) common to ISO 9001, ISO 27001, and ISO 22000.

### 6.2 Key Clauses

| Clause | Focus |
|--------|-------|
| Clause 4 | Context: organisational context, interested parties, AIMS scope |
| Clause 5 | Leadership: AI policy, roles, responsibilities, authority |
| Clause 6 | Planning: risk and opportunity identification, AI objectives |
| Clause 7 | Support: resources, competence, awareness, communication, documented information |
| Clause 8.2 | **AI Risk Assessment** — mandatory for all AI systems |
| Clause 8.3 | **AI Risk Treatment** — define and implement controls |
| Clause 8.4 | **AI System Impact Assessment** — impact on individuals and society |
| Clause 9 | Performance evaluation: monitoring, measurement, internal audit, management review |
| Clause 10 | Continual improvement: nonconformity, corrective action |

**Annex A Controls (10 categories):**

| Control | Focus |
|---------|-------|
| A.2 | AI policies — organisational AI policy alignment and review |
| A.3 | Internal organisation — AI roles, responsibilities, reporting |
| A.4 | Resources for AI systems — documentation, data, tooling, human resources |
| A.5 | Assessing impacts — impact assessment process, societal impact |
| A.6 | **AI system lifecycle** — development objectives, design, requirements, documentation, verification, validation, deployment, operation, monitoring, technical documentation, event logging |
| A.7 | Data for AI systems — acquisition, quality, provenance, preparation |
| A.8 | Information for interested parties — system documentation, external reporting, incident communication |
| A.9 | Responsible use of AI systems — intended use, objectives, responsible use processes |
| A.10 | Third-party and customer relationships — responsibility allocation, supplier management |

### 6.3 Risk Management Integration

**Clause 8.2 (AI Risk Assessment):** Risk assessments must address impact to: the organisation; individuals (e.g., lawyers and their clients); and society. Integrates with ISO/IEC 23894:2023 (AI Risk Management).

**Clause 8.4 (AI System Impact Assessment):** Formal assessment of potential impacts on individuals and society. Results shared with organisational leadership.

### 6.4 Relevance to Pickles GmbH

ISO/IEC 42001 is directly applicable to Pickles GmbH as an AI system provider. Key areas of relevance:

- **Clause A.6:** Full lifecycle documentation — design, development, deployment, monitoring — aligns with EU AI Act Article 11 technical documentation requirements
- **Clause A.7:** Data governance for AI training and validation data — aligns with EU AI Act Article 10
- **Clause A.9:** Responsible use documentation — aligns with BRAK human oversight requirements
- **Clause A.10:** Third-party model provider management — aligns with GDPR Article 28 sub-processor obligations and BRAK Section 43e BRAO requirements
- **Clauses 9-10:** Post-deployment monitoring and continual improvement — aligns with EU AI Act Article 72 post-market monitoring

### 6.5 Certification Pathway

| Pathway | Standard | Scope |
|---------|----------|-------|
| Management system certification | ISO/IEC 17021 | Clauses 4-10 — organisational AIMS |
| Product/service certification | ISO/IEC 17065 | Annex A controls — AI system-level conformance |

ISO/IEC 42001 certification may be used as evidence of governance maturity for enterprise legal clients and may support demonstration of EU AI Act quality management system requirements.

---

## 7. ENISA AI Cybersecurity Guidelines

**Source:** ENISA, "Threat Landscape for Artificial Intelligence" (December 2020), as read from `_input/ENISA-AI-cybersecurity-guidelines.pdf`

### 7.1 Scope

This document maps **cybersecurity threats to AI systems** across the AI lifecycle. Its primary relevance to this framework is as a threat intelligence source to inform security controls under GDPR Article 32 and EU AI Act Article 9 (risk management).

Three dimensions of AI cybersecurity:
1. **Cybersecurity for AI:** Protecting AI systems against attack
2. **AI to support cybersecurity:** Using AI as a defensive tool
3. **Malicious use of AI:** AI-powered attacks (deepfakes, social engineering, AI-powered malware)

### 7.2 AI Lifecycle Phases — Threat Surface

ENISA identifies 12 lifecycle phases across three groups:

| Group | Phases |
|-------|--------|
| Design and development | Business goal definition, data ingestion, data exploration, data pre-processing, feature selection, model selection/building |
| Training and tuning | Model training, model tuning |
| Deployment and operations | Transfer learning, model deployment, model maintenance, business understanding |

### 7.3 Key AI Threat Categories

| Category | Examples |
|----------|---------|
| **Data threats** | Data poisoning during ingestion; data quality failures; privacy violations during collection; data injection attacks |
| **Model threats** | Adversarial inference (input perturbations); model manipulation/evasion; model extraction; model inversion; backdoor and trojan attacks; membership inference |
| **Infrastructure and supply chain threats** | Compromised dependencies/libraries; third-party provider security failures; software supply chain integrity issues; hardware vulnerabilities |
| **Operational threats** | Insufficient logging and monitoring; lack of audit trails; model drift during deployment; retraining vulnerabilities; insufficient incident response |

### 7.4 Supply Chain and Third-Party AI Provider Risks

[ASSUMPTION — A-004] If Pickles GmbH uses third-party foundation model providers, the following risks apply:

**Data providers:** May collect data without user awareness; responsibility and liability for data mishandling must be allocated by contract; GDPR Article 28 DPA compliance must be verified.

**Model providers:** Responsibility for certification and operational monitoring must be documented; logging obligations must be assigned to a specific party in the supply chain; pre-trained model security must be assessed before integration.

**Cloud providers:** Data residency and transfer risk; multi-tenancy isolation; hardware vulnerabilities must be assessed.

### 7.5 Implied Controls for Legal AI

| Risk Area | Required Control |
|-----------|-----------------|
| Training data integrity | Validation of training, validation, and test data; data provenance tracking |
| Model robustness | Adversarial robustness testing; anomaly detection on outputs |
| Post-deployment monitoring | Event logging and audit trails; model drift detection; incident response protocols |
| Supply chain security | Vendor/provider security assessments; software dependency scanning; DPA and contractual coverage |

### 7.6 Alignment with GDPR

ENISA explicitly notes that AI security obligations align with GDPR Article 32 security requirements and that appropriate security measures "should be introduced at the **design phase** of new applications" in line with GDPR Article 25 (data protection by design). This confirms that security and data protection design must be concurrent, not sequential.

---

## 8. Concluding Regulatory Obligations Checklist

Based on the source documents above, the governance framework for Pickles GmbH must address the following regulatory obligations. This checklist structures the work for Stages 2-5.

### 8.1 EU AI Act

| Ref | Obligation | Regulatory Basis | Target Stage |
|----|-----------|-----------------|-------------|
| EU-1 | Determine risk classification (high-risk / limited-risk / minimal) for each AI system | Art. 6, Annex III, Recitals 53 and 61 | Stage 2 |
| EU-2 | Produce technical documentation for all high-risk systems | Art. 11 | Stage 3 |
| EU-3 | Implement continuous AI risk management system across full lifecycle | Art. 9 | Stage 2/3 |
| EU-4 | Implement data quality and governance controls for training, validation, and test datasets | Art. 10 | Stage 3 |
| EU-5 | Design and operationalise human oversight for all high-risk systems; prohibit fully automated legal decisions | Art. 14 | Stage 2 |
| EU-6 | Implement automatic event logging for all high-risk systems | Art. 12 | Stage 3/4 |
| EU-7 | Produce clear instructions for use covering characteristics, capabilities, and limitations | Art. 13 | Stage 3 |
| EU-8 | Implement AI-human interaction disclosure (users informed they are interacting with AI) | Art. 50 | Stage 3 |
| EU-9 | Implement AI-generated content labelling obligations (from 2 August 2026) | Art. 50 | Stage 3/5 |
| EU-10 | Perform conformity assessment and draw up Declaration of Conformity for high-risk systems | Arts. 16-23 | Stage 3 |
| EU-11 | Establish post-market monitoring system; report serious incidents | Art. 72 | Stage 4 |
| EU-12 | Establish substantial modification tracking and re-assessment process | Art. 3 | Stage 4 |
| EU-13 | Implement AI competence measures for all staff involved in AI system operation | Art. 4 (in force from 2 Feb 2025) | Stage 2 |

### 8.2 GDPR

| Ref | Obligation | Regulatory Basis | Target Stage |
|----|-----------|-----------------|-------------|
| GDPR-1 | Execute GDPR-compliant Data Processing Agreements (DPAs) with all lawyer clients | Art. 28 | Stage 3/5 |
| GDPR-2 | Conduct DPIA for all systems processing personal data at high risk | Art. 35 | Stage 3 |
| GDPR-3 | Implement prior consultation with supervisory authority where DPIA shows high residual risk | Art. 36 | Stage 3 |
| GDPR-4 | Implement data subject rights handling procedures (access, erasure, portability, etc.) | Arts. 12-22 | Stage 2/3 |
| GDPR-5 | Prohibit fully automated decisions with legal effects without appropriate human intervention safeguards | Art. 22 | Stage 2 |
| GDPR-6 | Implement data protection by design and by default across all product development | Art. 25 | Stage 2/3 |
| GDPR-7 | Implement appropriate security measures including encryption, resilience, and regular testing | Art. 32 | Stage 3/4 |
| GDPR-8 | Establish data breach detection, notification procedures (72-hour rule), and documentation | Art. 33 | Stage 4 |
| GDPR-9 | Identify and implement appropriate mechanism for all international data transfers | Arts. 44-49 | Stage 3 |
| GDPR-10 | Disclose existence of automated decision-making in transparency notices | Arts. 13(2)(f), 14(2)(g) | Stage 3 |
| GDPR-11 | Implement consent management system if consent is used as legal basis for any processing | Arts. 7, 17; EDPB Guidelines 05/2020 | Stage 3 |

### 8.3 BDSG (German Law)

| Ref | Obligation | Regulatory Basis | Target Stage |
|----|-----------|-----------------|-------------|
| BDSG-1 | Designate DPO if 20+ staff perform automated personal data processing (or if DPIA is undertaken) | BDSG Section 38 | Stage 2 |
| BDSG-2 | Conduct BDSG DPIA for all new AI systems processing personal data with substantial risk | BDSG Section 67 | Stage 3 |
| BDSG-3 | Prior consultation with BfDI where BDSG DPIA indicates substantial residual risk | BDSG Section 69 | Stage 3 |
| BDSG-4 | Implement Section 64 BDSG technical controls for all automated processing systems | BDSG Section 64 | Stage 3/4 |
| BDSG-5 | Implement mandatory audit logging of all CRUD operations in automated systems; 1-year retention | BDSG Section 76 | Stage 3/4 |
| BDSG-6 | Apply Section 29 BDSG professional confidentiality restrictions on data subject rights responses | BDSG Section 29 | Stage 3 |

### 8.4 BRAK / Professional Conduct

| Ref | Obligation | Regulatory Basis | Target Stage |
|----|-----------|-----------------|-------------|
| BRAK-1 | Design all AI systems to require human review — never to replace lawyer judgment | BRAK Position Paper, Section 2.1; Section 43(1) BRAO | Stage 2 |
| BRAK-2 | Ensure AI systems never imply legal review by the lawyer is unnecessary | BRAK Position Paper, Section 2.2 | Stage 3 |
| BRAK-3 | Design and document data handling workflows supporting client document anonymisation before upload | BRAK Position Paper, Section 3.1; Section 43a(2) BRAO | Stage 3 |
| BRAK-4 | Provide Section 43e BRAO-compliant service agreements covering confidentiality obligations and purpose limitation | Section 43e(2), (3) BRAO | Stage 3/5 |
| BRAK-5 | Assess and document confidentiality-equivalent protection for all third-country AI model providers | Section 43e(4) BRAO | Stage 3 |
| BRAK-6 | Implement AI output labelling requirements (EU AI Act Article 50 — from 2 August 2026) | Art. 50 EU AI Act; BRAK Position Paper, Section 5.2 | Stage 3/5 |
| BRAK-7 | Provide client training and documentation materials supporting lawyer AI competence obligations | Art. 4 EU AI Act; BRAK Position Paper, Section 5.1 | Stage 5 |
| BRAK-8 | Establish monitoring process for BRAK guidance updates (guidance is explicitly flagged as a "snapshot") | BRAK Position Paper, Section 8 | Stage 4 |

### 8.5 ISO/IEC 42001 and ENISA

| Ref | Obligation | Regulatory Basis | Target Stage |
|----|-----------|-----------------|-------------|
| ISO-1 | Establish AI Management System aligned with ISO/IEC 42001 Clauses 4-10 | ISO/IEC 42001 | Stage 2 |
| ISO-2 | Conduct formal AI system impact assessments per Clause 8.4 | ISO/IEC 42001, Clause 8.4 | Stage 3 |
| ISO-3 | Implement AI lifecycle documentation and controls per Annex A Clause A.6 | ISO/IEC 42001, Annex A | Stage 2/3 |
| ISO-4 | Manage third-party AI model provider relationships per Clause A.10 | ISO/IEC 42001, Annex A | Stage 3 |
| ENISA-1 | Conduct supply chain security assessment for all AI model providers and cloud infrastructure | ENISA Threat Landscape, Section 2.2 (AI Lifecycle Actors) | Stage 3 |
| ENISA-2 | Implement adversarial robustness testing as part of model validation | ENISA Threat Landscape, threat taxonomy | Stage 3/4 |
| ENISA-3 | Implement comprehensive event logging and audit trails across full AI lifecycle | ENISA Threat Landscape, threat taxonomy (Annex B, Operational threats) | Stage 3/4 |
| ENISA-4 | Implement model drift monitoring and post-deployment performance review | ENISA Threat Landscape, Section 2.3, Phase 11 (Model Maintenance) | Stage 4 |

---

## Appendix: Regulatory Assumptions Flagged in This Document

The following assumptions are flagged for verification. All are marked [ASSUMPTION] in the document body. The governance framework is built on these until they are confirmed against real Pickles GmbH data.

| Code | Assumption | Status | Key Sections |
|------|-----------|--------|-------------|
| A-001 | Pickles GmbH provides legal AI covering drafting, research, summarisation, analysis | 🔴 Unverified | 1.2, 2.4, 5.2 |
| A-002 | Clients are German legal professionals or in-house legal departments | 🔴 Unverified | 5 (BRAK) throughout |
| A-003 | Pickles GmbH operates under EU AI Act, GDPR, BDSG, and BRAK standards | 🔴 Unverified | Opening |
| A-004 | Third-party AI model providers may be in use | 🔴 Unverified | 2.8, 5.4, 7.4 |
| A-005 | Hosting is EU-based | 🔴 Unverified | 2.8 |
| A-006 | Pickles GmbH's products include client-facing AI interaction interfaces | 🔴 Unverified | 1.4 |
| A-007 | Pickles GmbH acts as data processor for lawyer clients (not joint controller or independent controller) | 🔴 Unverified | 2.2, 2.4 |
| A-008 | Pickles GmbH employs 20+ staff with automated data processing roles | 🔴 Unverified | 3.2 |

---

> *This document is a proposal. It is not a legal compliance certification. All regulatory conclusions are drawn from source documents in `_input/` as of 2026-02-22. Before any part of this document is used as the basis for operational decisions, it must be reviewed by a qualified German lawyer with expertise in data protection law, AI regulation, and professional conduct regulation.*
>
> [LEGAL REVIEW REQUIRED] — This document as a whole requires professional legal review before operational use.
