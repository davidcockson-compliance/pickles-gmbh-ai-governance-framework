# P2-Worked-Example-Technical-Documentation-v1.md

**Project:** Pickles GmbH — AI Governance Framework
**Stage:** Phase 2 — Worked Example
**Document type:** Technical Documentation Pack (EU AI Act Article 11 / Annex IV)
**System:** Vertrag.AI — Contract Review Assistant
**Status:** Draft
**Version:** v1
**Date:** 2026-02-28
**Assumptions:** Built on Phase 2 worked example assumptions — Vertrag.AI is a fictional system. All technical parameters are illustrative. Requires population with real system data before operational use.

---

## Document Purpose

This document constitutes the Technical Documentation Pack for Vertrag.AI, prepared in accordance with the obligations framework established in `P2-Worked-Example-EU-AI-Act-Mapping-v1.md`.

Vertrag.AI is classified as **limited risk** under the EU AI Act (Article 52 transparency obligations apply) with an **internal classification of Medium-High** due to professional liability exposure in the German legal market. This documentation pack is maintained as a proportionate governance control aligned with that internal classification, and as preparation for potential reclassification if the system's scope or capabilities expand.

The structure follows the Annex IV template from the EU AI Act, adapted for a limited-risk system. Sections are populated with realistic illustrative content. Where real system data would be required, this is explicitly flagged.

> **Note for implementers:** If Vertrag.AI or an equivalent system were classified as high risk under Annex III, this document would become a mandatory compliance artefact. At limited-risk classification, it is a voluntary governance control. The decision to maintain it regardless reflects the professional liability context of the German legal market and the internal Medium-High risk rating.

---

## Section 1 — System Description and Intended Purpose

### 1.1 System Name and Version

| Field | Value |
|---|---|
| System name | Vertrag.AI |
| Current version | v1.0 (illustrative) |
| Deployment type | B2B SaaS — cloud-hosted, multi-tenant |
| System owner | [Product Lead — to be confirmed] |
| Technical owner | [Head of Engineering — to be confirmed] |
| Documentation maintained by | Compliance function |
| Last reviewed | 2026-02-28 |

### 1.2 Intended Purpose

Vertrag.AI is a contract review assistant designed for use by qualified lawyers at German law firms. The system assists with the review of commercial contracts, identifying potentially problematic clauses and producing a redlined version of the contract document.

**Primary use case:** Pre-signature review of commercial contracts on behalf of a law firm's clients. The system analyses a contract uploaded by a lawyer, identifies clauses that warrant attention (non-standard terms, missing provisions, unfavourable risk allocation), and produces a redlined DOCX output. The lawyer reviews and accepts or rejects redline suggestions before any output is used or shared.

**Secondary use case:** Post-signature contract analysis — reviewing executed contracts to identify obligations, deadlines, and renewal triggers.

**Intended user population:** Qualified German lawyers (*Rechtsanwälte*) operating within German law firms. The system is not intended for use by non-lawyers, legal assistants without lawyer supervision, or clients directly.

**Intended use context:** The system operates as a professional support tool. It does not provide legal advice. All outputs require mandatory lawyer review before use. The responsible lawyer retains full professional responsibility for any advice given to the client.

### 1.3 What the System Is Not Intended To Do

- Provide legal advice directly to clients
- Generate final client-deliverable documents without lawyer review
- Make autonomous decisions about contract acceptability
- Replace the professional judgment of the reviewing lawyer
- Operate without a qualified lawyer in the review loop

---

## Section 2 — Model Architecture and Technical Design

### 2.1 Architecture Overview

Vertrag.AI is built on a retrieval-augmented generation (RAG) architecture combining a commercial large language model API with a curated legal knowledge base.

```
[Lawyer uploads contract DOCX]
        |
        v
[Document Parser — extract text, structure, clause segmentation]
        |
        v
[RAG Retrieval Layer — query German legal corpus for relevant standards/precedents]
        |
        v
[Prompt Construction — system prompt + contract text + retrieved context]
        |
        v
[LLM API Call — Claude claude-sonnet-4-20250514 via Anthropic API]
        |
        v
[Output Parser — structure redline suggestions, assign clause references]
        |
        v
[DOCX Generator — produce redlined contract document]
        |
        v
[Lawyer review interface — accept / reject / modify each suggestion]
        |
        v
[Final DOCX export — accepted changes only]
```

**Assumption:** Architecture is illustrative based on Anthropic's legal productivity GitHub examples adapted for German law context. Real system architecture to be confirmed and documented.

### 2.2 Model Provider

| Field | Value |
|---|---|
| Model provider | Anthropic |
| Model | Claude (claude-sonnet-4-20250514 or equivalent at time of deployment) |
| Access method | Anthropic API |
| Fine-tuning applied | No — base model with structured prompting |
| System prompt | Yes — governs output format, task framing, and professional context |

**Assumption:** Anthropic is the model provider. Data Processing Agreement with Anthropic required — flagged as Compliance Gap 6 in the EU AI Act Mapping document. Model selection and versioning policy to be confirmed.

### 2.3 RAG Knowledge Base

| Field | Value |
|---|---|
| Knowledge base content | German civil law standards, standard commercial contract terms, BGB provisions, common clause formulations |
| Knowledge base format | Indexed vector store |
| Update frequency | [To be confirmed — assumed quarterly] |
| Curation responsibility | [Legal content team — to be confirmed] |
| Version control | [To be confirmed] |

**Assumption:** The RAG knowledge base is maintained by Pickles GmbH. Its composition, update cadence, and quality controls require documentation. This is a significant governance gap — knowledge base quality directly affects output accuracy.

### 2.4 Hosting and Infrastructure

| Field | Value |
|---|---|
| Hosting provider | [EU-based cloud provider — to be confirmed] |
| Hosting region | [EU — assumed, unconfirmed] |
| Data residency | [EU — assumed, unconfirmed] |
| Multi-tenancy model | Logical separation — dedicated data store per client organisation |
| Authentication | [SSO / MFA — to be confirmed] |

**Assumption:** EU hosting assumed. This affects GDPR adequacy position and client data handling obligations. Must be confirmed before client-facing documentation is finalised.

---

## Section 3 — Training Data and Knowledge Base

### 3.1 Base Model Training Data

Vertrag.AI uses the Anthropic Claude base model without fine-tuning. Anthropic's model training data documentation governs this component. Pickles GmbH does not have direct visibility into base model training data composition.

**Implication:** Pickles GmbH should maintain reference to Anthropic's published model cards and usage policies as part of its vendor documentation. Any changes to the underlying model (version updates, architecture changes) should trigger review under the Model Change Management Protocol.

### 3.2 RAG Knowledge Base — Provenance and Curation

The RAG knowledge base constitutes the primary domain-specific knowledge layer of the system. Its quality directly determines the relevance and accuracy of retrieved context used in generating redline suggestions.

| Field | Value |
|---|---|
| Content categories | BGB statutory text, standard AGB formulations, BRAK professional guidance, sector-specific contract templates |
| Source types | Official German legal publications, publicly available legal standards, internally curated precedent library |
| Language | German (primary), English (secondary for international contract review) |
| Coverage scope | Commercial contracts — M&A, service agreements, supply chain, employment, real estate |
| Exclusions | Consumer contracts, regulatory matters, court filings |
| Curation process | [To be defined — legal content review before indexing] |
| Quality controls | [To be defined] |

**Assumption:** Knowledge base composition is assumed. Formal curation policy, source documentation, and version control for the knowledge base are required governance artefacts. These do not currently exist (assumed).

### 3.3 Known Data Gaps and Limitations

The following limitations are assumed to apply and should be confirmed and documented:

- Coverage of highly specialist contract types (e.g. joint ventures, complex financial instruments) may be incomplete
- Knowledge base reflects a point-in-time view — recently enacted legislation or case law may not be indexed
- English-language contracts may receive less accurate review due to German-corpus bias
- Non-standard contract structures may not retrieve well from the vector index

---

## Section 4 — Testing and Validation Methodology

### 4.1 Pre-Deployment Testing Requirements

The following testing categories are required before any new version of Vertrag.AI is deployed to production. This section documents the required methodology; actual test results should be maintained as a separate test log.

**Assumption:** Testing methodology described here is proposed. Actual test protocols to be designed and confirmed by the engineering team.

#### Functional Accuracy Testing

| Test type | Description | Pass criterion |
|---|---|---|
| Clause identification accuracy | Sample contracts with known issues reviewed; system output compared to lawyer-prepared baseline | ≥85% of known issues identified |
| False positive rate | Clean contracts reviewed; count of spurious redline suggestions | ≤15% of suggestions flagged as spurious by reviewing lawyers |
| Citation accuracy | BGB and legal standard references in system output checked against source texts | 100% of cited provisions must exist and be correctly described |
| Output format validation | Redlined DOCX output verified for structural integrity | 100% of outputs open correctly in Microsoft Word and LibreOffice |

#### Adversarial and Edge Case Testing

| Test type | Description |
|---|---|
| Unusual contract structures | Non-standard formatting, missing clause headings, very long documents |
| Mixed language contracts | German/English bilingual contracts |
| Contracts with deliberate errors | Test whether system identifies genuine issues or generates noise |
| Empty or corrupt inputs | System behaviour on invalid file uploads |

#### Human Review Bypass Testing

Verify that the system architecture does not permit output to reach a client without passing through the lawyer review interface. This is a hard requirement — any pathway that bypasses mandatory review is a critical defect.

### 4.2 Ongoing Quality Monitoring

See `P2-Worked-Example-Monitoring-Entry-v1.md` for the live monitoring framework. Testing and monitoring should be treated as connected — monitoring data from production use should feed back into test case development.

### 4.3 Model Change Retesting Requirements

When the underlying model version changes (e.g. Anthropic releases a new Claude version), the following minimum retesting is required before deployment:

- Full functional accuracy test suite
- Citation accuracy test
- Output format validation
- Sample comparison between old and new model output on the same test contracts

---

## Section 5 — Known Limitations and Risk Controls

### 5.1 Known Limitations

The following limitations are inherent to the system design and must be disclosed to users as part of onboarding and within the product interface.

| Limitation | Description | Mitigation |
|---|---|---|
| Not legal advice | System output is analytical assistance, not legal advice | Mandatory disclosure in UI and terms of service |
| Knowledge base currency | RAG corpus reflects point-in-time legal landscape | Knowledge base update cadence and version disclosure |
| Hallucination risk | LLM may generate plausible but incorrect legal references | Mandatory lawyer review; citation spot-check functionality |
| Coverage gaps | Some specialist contract types underserved | Scope disclosure in product documentation |
| Language limitations | German-primary; English and other languages less accurate | Language scope disclosure |
| No autonomous action | System cannot execute, sign, or submit any document | Architectural control — output is DOCX only |

### 5.2 Hallucination Risk — Specific Controls

Hallucination (generation of false but plausible legal references) is the highest-consequence output risk for Vertrag.AI. The following controls apply:

- **Mandatory lawyer review:** Every output requires a qualified lawyer to review before any use. This is the primary control and must never be removed or made optional.
- **Citation flagging:** Where the system cites a specific BGB article, AGB standard, or other provision, the UI should provide a mechanism to verify the citation. Implementation of this feature is a compliance priority (Compliance Gap 5 from EU AI Act Mapping).
- **Confidence indicators:** Where the system has lower retrieval confidence, this should be surfaced to the reviewing lawyer. Implementation status: to be confirmed.
- **User training:** All firm users must complete onboarding covering hallucination risk and how to spot unreliable outputs.

### 5.3 Professional Liability Boundary

Vertrag.AI operates in an environment where the reviewing lawyer retains full professional responsibility under BRAK rules and German professional liability law. The system does not assume, transfer, or share professional responsibility.

This boundary must be maintained clearly in:
- Terms of service with law firm clients
- User interface disclosures
- Training materials
- Any client-facing documentation about the system

---

## Section 6 — Human Oversight Design

### 6.1 Oversight Architecture

Human oversight is structural, not procedural — it is built into the system architecture so that lawyer review cannot be bypassed.

```
AI output → Staging layer (not client-deliverable)
                    |
                    v
         Lawyer review interface
         [Accept / Reject / Modify each suggestion]
                    |
                    v
         Accepted output only → DOCX export
                    |
                    v
         Lawyer applies professional judgment
         before any client use
```

There is no pathway from AI output to client-deliverable document that does not pass through the lawyer review step.

### 6.2 Mandatory Review Requirements

| Requirement | Implementation |
|---|---|
| All suggestions must be individually reviewed | Review interface requires explicit accept/reject/modify for each flagged clause |
| Bulk acceptance without review is not permitted | [To be confirmed — UI design requirement] |
| Export requires review completion | [To be confirmed — system gate before DOCX export] |
| Reviewer identity is logged | Audit log records which user reviewed and when |

**Assumption:** UI design requirements listed here are intended design specifications. Confirmation of implementation required from engineering team.

### 6.3 User Qualification Requirements

The system is restricted to qualified lawyers (*Rechtsanwälte*). Access controls should enforce this:

- Firm-level onboarding confirms all users are qualified lawyers or supervised trainees with lawyer oversight
- User terms require disclosure if access is shared with unqualified personnel
- Account provisioning is via firm administrators, not individual sign-up

**Assumption:** Access control model is assumed. Implementation details to be confirmed.

---

## Section 7 — Logging and Traceability

### 7.1 Audit Log Requirements

The following events must be logged to support incident investigation, quality monitoring, and regulatory enquiry response.

| Event | Log content | Retention |
|---|---|---|
| Contract upload | Session ID, user ID, firm ID, file hash (not file content), timestamp | 24 months |
| System query | Session ID, timestamp, model version, RAG retrieval summary (not full prompt) | 24 months |
| Review action | Session ID, user ID, each accept/reject/modify action, timestamp | 24 months |
| Export | Session ID, user ID, timestamp, output file hash | 24 months |
| Error or exception | Session ID, error type, timestamp | 24 months |
| Model version change | Old version, new version, deployment timestamp, authorising user | Indefinite |

**Assumption:** Retention period of 24 months assumed as proportionate. GDPR Article 5(1)(e) storage limitation principle applies — retention must be justified by legitimate purpose. Legal review of retention periods recommended.

### 7.2 What Is Not Logged

The following must not be captured in system logs to comply with GDPR and confidentiality obligations:

- Full contract text uploaded by users
- Full system prompt content passed to the model
- Client names or matter details
- Any personal data beyond user ID and firm ID
- Legally privileged communications

**Note:** This creates a tension with incident investigation capability. If a quality incident occurs, the absence of full prompt/contract logs limits root cause analysis. This tension is inherent to the GDPR/confidentiality constraints of the legal market and must be acknowledged in the incident response playbook.

### 7.3 Traceability for Output Review

Each redline suggestion in the lawyer review interface should carry:
- Reference to the retrieved RAG source(s) that informed the suggestion (at minimum: knowledge base category and retrieval score)
- The specific contract clause to which the suggestion applies
- The model version that generated the suggestion

This supports lawyer review quality and provides traceability if a suggestion is later challenged.

---

## Section 8 — GDPR and Data Handling

### 8.1 Personal Data Processing

Vertrag.AI processes the following categories of data:

| Data category | Nature | Legal basis |
|---|---|---|
| User account data | Name, email, firm affiliation | Contract (Article 6(1)(b) GDPR) |
| Usage metadata | Session logs, review actions | Legitimate interests (Article 6(1)(f) GDPR) — subject to balancing test |
| Uploaded contract content | Potentially contains personal data about third parties | Processor role — law firm is controller |
| AI-generated output | Redline suggestions — no personal data | N/A |

**Assumption:** Legal basis analysis is indicative. GDPR data protection impact assessment (DPIA) required given processing of potentially sensitive legal documents. Flagged as Compliance Gap 3 in EU AI Act Mapping.

### 8.2 Sub-Processor: Anthropic

All prompts sent to the Claude API are processed by Anthropic as a sub-processor. This has significant implications:

- Data Processing Agreement with Anthropic is required under GDPR Article 28
- Data transfer mechanisms for any processing outside the EU must be confirmed
- Anthropic's data retention and training data policies must be reviewed and documented
- Client-facing DPA with law firms must disclose Anthropic as a sub-processor

**Assumption:** Anthropic sub-processor relationship assumed based on API usage. DPA status unconfirmed. This is Compliance Gap 6 in the EU AI Act Mapping — high priority.

### 8.3 Law Firm as Data Controller

When a law firm uses Vertrag.AI to review contracts on behalf of its clients, the law firm is the data controller for any personal data within those contracts. Pickles GmbH acts as data processor.

Implications:
- Client contract (DPA) must be in place before any law firm can upload contracts
- Law firms must have obtained appropriate authority from their clients to process contract data in a cloud AI system
- Confidentiality obligations under BRAK rules apply to the law firm — Pickles GmbH's infrastructure must support confidentiality compliance

---

## Section 9 — Assumptions Register (This Document)

The following assumptions are embedded in this document and require validation before this documentation is used operationally.

| ID | Assumption | Section | Priority |
|---|---|---|---|
| TD-A-01 | Anthropic Claude is the model provider | 2.2 | High |
| TD-A-02 | RAG architecture as described | 2.1 | High |
| TD-A-03 | EU-based hosting | 2.4 | High |
| TD-A-04 | No fine-tuning applied to base model | 2.2 | Medium |
| TD-A-05 | Knowledge base composition as described | 3.2 | High |
| TD-A-06 | Quarterly knowledge base update cadence | 3.2 | Low |
| TD-A-07 | Functional accuracy testing not yet conducted | 4.1 | High |
| TD-A-08 | Lawyer review UI prevents bulk acceptance | 6.2 | High |
| TD-A-09 | GDPR retention periods as specified | 7.1 | Medium |
| TD-A-10 | No DPA with Anthropic currently in place | 8.2 | High |

---

## Section 10 — Document Control and Review Schedule

| Field | Value |
|---|---|
| Document owner | Compliance function |
| Technical reviewer | Head of Engineering |
| Legal reviewer | General Counsel / external German legal counsel |
| Review trigger events | Model version change; material architecture change; new use case; annual scheduled review |
| Annual review date | [Set on first deployment] |
| Version history | v1 — initial draft (2026-02-28) |

**Note:** This document requires review by a qualified German lawyer and a data protection specialist before it is used as a compliance artefact. The current draft is a governance framework demonstration and contains assumptions throughout.

---

*End of P2-Worked-Example-Technical-Documentation-v1.md*