# P2 Worked Example — System Profile: Vertrag.AI

**Project:** Pickles GmbH — AI Governance Framework
**Stage:** Phase 2 — Worked Example
**Document:** P2-Worked-Example-System-Profile-v1.md
**Status:** Draft
**Version:** v1
**Date:** 2026-02-28
**Assumptions:** Built on Phase 2 fictional system design — Vertrag.AI does not exist. All system characteristics are illustrative. Not verified against real company data.

---

## About This Document

This document populates the Pickles GmbH AI System Inventory template (L1-3.1) with a fully worked entry for **Vertrag.AI**, a fictional contract review tool operated by Pickles GmbH for German law firm clients. It demonstrates how the inventory framework functions against realistic system content.

All fields follow the structure defined in L1-3.1-AI-System-Inventory-v1.md. Where that template requires [ASSUMPTION] flags, they are carried through here with content populated.

---

## 1. System Identification

| Field | Entry |
|---|---|
| **System Name** | Vertrag.AI |
| **System ID** | PKL-SYS-003 |
| **System Owner** | Head of Product, Pickles GmbH |
| **Technical Lead** | Senior ML Engineer, Pickles GmbH [ASSUMPTION: role exists; name not assigned in fictional design] |
| **Date Registered** | 2026-02-28 |
| **Record Last Updated** | 2026-02-28 |
| **Deployment Status** | Production |

---

## 2. System Description

### 2.1 Purpose and Function

Vertrag.AI is a B2B SaaS contract review tool designed for German law firms reviewing contracts on behalf of clients. The system analyses uploaded contract documents, identifies legally significant clauses, surfaces risk flags, and produces a redlined output with AI-drafted suggested clause amendments. Lawyer review and approval is required before any amended output is used or shared with clients.

The system supports two primary workflow positions:

- **Pre-signature review:** The law firm uploads a contract prior to client execution. Vertrag.AI produces a risk-flagged analysis and redlined suggested amendments. The supervising lawyer reviews, accepts or rejects suggested changes, and provides final advice to the client.
- **Post-signature audit:** The law firm uploads an existing contract from a client's portfolio. Vertrag.AI analyses obligations, risk exposure, and potential issues for ongoing portfolio management or dispute preparation.

### 2.2 User Population

| User Type | Description |
|---|---|
| Primary users | Qualified lawyers (Rechtsanwälte) and legal assistants at German law firms |
| Indirect affected parties | Law firm clients (natural persons and legal entities) whose contracts are reviewed using the system |
| Excluded users | Members of the public; individuals without a law firm account |

### 2.3 Operational Context

Vertrag.AI is accessed via a web application hosted on EU-based cloud infrastructure [ASSUMPTION: EU hosting confirmed in fictional design; hosting provider not specified]. Law firm users authenticate via single sign-on (SSO) linked to the firm's Pickles GmbH account. Contracts are uploaded as PDF or DOCX files. The system processes the document, returns analysis and a redlined DOCX output, and stores both within the user's account workspace. No AI-generated output is transmitted directly to the law firm's clients — output is intermediated by the supervising lawyer.

---

## 3. Technical Architecture

### 3.1 System Type

| Field | Entry |
|---|---|
| **AI System Category** | Generative AI — Large Language Model (LLM) with Retrieval-Augmented Generation (RAG) |
| **Model Provider** | Anthropic (Claude API) [ASSUMPTION: API access via standard commercial agreement; data processing agreement in place] |
| **Model Version Policy** | Pinned to a specific Claude model version; version changes require internal change management sign-off before deployment |
| **RAG Layer** | Yes — retrieval layer over a curated corpus of German legal sources (see Section 3.3) |
| **Fine-tuning** | No fine-tuning applied to base model [ASSUMPTION] |
| **Self-hosted components** | RAG retrieval infrastructure, document pre-processing pipeline, output formatting layer |

### 3.2 Data Flow Summary

```
User uploads contract (PDF/DOCX)
        ↓
Document pre-processing pipeline
(extraction, chunking, format normalisation)
        ↓
RAG retrieval layer
(relevant German legal corpus passages retrieved)
        ↓
Prompt construction
(system prompt + contract content + retrieved legal context)
        ↓
Claude API (Anthropic)
(analysis generated; clause amendments drafted)
        ↓
Output post-processing
(redlined DOCX generated; risk flags structured)
        ↓
Result stored in user workspace
        ↓
Lawyer reviews, accepts/rejects amendments
        ↓
Final document used or discarded — lawyer's decision
```

[ASSUMPTION: Data flow above reflects intended architectural design. Actual implementation details would require verification with CTO/engineering lead.]

### 3.3 RAG Corpus — German Legal Sources

The retrieval layer draws from a curated corpus maintained by Pickles GmbH. [ASSUMPTION: Corpus composition below is illustrative; actual sources would require verification.]

| Source Type | Examples |
|---|---|
| German statutory law | BGB (Bürgerliches Gesetzbuch), HGB (Handelsgesetzbuch), selected sector statutes |
| German case law summaries | BGH (Bundesgerichtshof) case summaries — selected landmark decisions |
| Standard contract clause libraries | BRAK guidance on standard terms; AGB (Allgemeine Geschäftsbedingungen) reference materials |
| Academic commentary summaries | Curated excerpts from major German civil law commentaries |

**Corpus maintenance:** The corpus is reviewed and updated on a defined schedule. [ASSUMPTION: Quarterly review cycle — requires confirmation.] Updates follow the Model Change Management Protocol (L3-6.3).

### 3.4 Hosting and Infrastructure

| Field | Entry |
|---|---|
| **Primary hosting location** | EU (Germany) [ASSUMPTION] |
| **Cloud provider** | Not specified in fictional design [ASSUMPTION: major EU-compliant provider] |
| **Data residency** | All contract data remains within EEA [ASSUMPTION] |
| **Anthropic API data processing** | Governed by Anthropic's data processing agreement; prompts not used for model training under commercial API terms [ASSUMPTION: DPA reviewed and confirms this] |
| **Encryption** | TLS 1.2+ in transit; AES-256 at rest [ASSUMPTION] |

---

## 4. Data Categories Processed

| Data Category | Description | GDPR Relevance |
|---|---|---|
| Contract documents | PDF/DOCX files uploaded by law firm users | May contain personal data of third parties (counterparties, individuals named in contracts) |
| Personal data of natural persons | Names, addresses, signatures, identification references within contract documents | Article 4(1) GDPR — personal data |
| Potentially sensitive personal data | Some contracts may reference health, employment, family, or financial matters | Article 9 GDPR — special categories possible depending on contract type |
| Legal professional privilege material | Contracts reviewed in the context of a lawyer-client relationship | BRAK professional confidentiality obligations apply |
| Law firm user account data | Login credentials, usage logs, account metadata | Standard personal data under GDPR Article 4(1) |

**Key data protection note:** Contract documents uploaded to Vertrag.AI are processed by the Claude API (Anthropic). This constitutes a transfer of potentially personal data to a sub-processor. A Data Processing Agreement must be in place with Anthropic, and the law firm client must be informed of sub-processor involvement via Pickles GmbH's data processing terms. [Requires review by qualified lawyer before operational use.]

---

## 5. Risk Classification

### 5.1 Preliminary Classification

| Classification Dimension | Assessment |
|---|---|
| **EU AI Act risk tier** | Limited risk (Article 52) — transparency obligations apply; system does not fall within Annex III high-risk categories as currently designed [see note below] |
| **Pickles GmbH internal risk tier** | Medium-High |
| **Professional liability exposure** | High — output feeds into legal advice given to clients of a regulated profession |
| **Automation level** | Assisted decision-making — all outputs require mandatory human review and approval before use |

**EU AI Act classification note:** Vertrag.AI does not appear to fall within the Annex III high-risk categories as defined in EU AI Act Regulation (EU) 2024/1689. The system does not make autonomous decisions affecting individuals' legal rights; all output is reviewed by a qualified lawyer before any client-facing use. However, the system processes legal content that could, if misused, influence legal outcomes affecting natural persons. This classification should be reviewed by a qualified lawyer and reassessed if the product roadmap moves toward greater automation. [Flag for legal review before operational use.]

### 5.2 Internal Risk Factors

The following factors elevate Vertrag.AI's internal risk rating above low:

- Output is used in legal advice to clients — errors carry professional liability consequences for the law firm
- The system processes legally privileged material and potentially sensitive personal data
- German professional conduct rules (BRAK) impose obligations on lawyers using AI tools
- RAG corpus quality directly affects output accuracy — corpus drift or gaps could produce systematically incorrect advice
- Law firm clients may not be independently aware that AI has been used in their matter unless disclosed

---

## 6. Human Oversight Design

| Oversight Element | Design |
|---|---|
| **Mandatory review gate** | All Vertrag.AI output is presented as a draft requiring lawyer review — no output is transmitted to clients without a supervising lawyer's approval |
| **Output labelling** | All AI-generated suggested amendments are visually marked as AI-drafted in the redlined DOCX; the system does not produce clean documents without lawyer action |
| **Disclaimer in product UI** | Persistent UI notice confirms that output constitutes AI-assisted analysis only and does not constitute legal advice |
| **Audit trail** | All system outputs, lawyer actions (accept/reject), and timestamps are logged per session |
| **Override capability** | Lawyers can reject any or all AI-suggested amendments; the system cannot override lawyer decisions |

[ASSUMPTION: Oversight design above reflects intended product behaviour. Verification against actual product specification required.]

---

## 7. Monitoring Status

| Field | Entry |
|---|---|
| **Monitoring in place** | Yes — see P2-Worked-Example-Monitoring-Entry-v1.md for full monitoring framework entry |
| **Key metrics tracked** | Clause amendment acceptance rate; risk flag accuracy (sampled); user-reported error rate; API error rate; RAG retrieval quality indicators |
| **Incident log** | Active — no incidents recorded in fictional design |
| **Last monitoring review** | Not yet established (system newly registered in fictional design) |

---

## 8. Regulatory and Compliance Cross-References

| Framework | Relevance | Cross-Reference Document |
|---|---|---|
| EU AI Act (Regulation (EU) 2024/1689) | Transparency obligations (Article 52); provider obligations (Article 16 if high-risk classification confirmed) | P2-Worked-Example-EU-AI-Act-Mapping-v1.md |
| GDPR (Regulation (EU) 2016/679) | Personal data in contracts; sub-processor relationship with Anthropic; data subject rights | L2-5.1-GDPR-Alignment-Framework-v1.md |
| BDSG (Bundesdatenschutzgesetz) | German national data protection overlay | L2-5.1-GDPR-Alignment-Framework-v1.md |
| BRAK professional standards | Lawyer obligations when using AI tools; client confidentiality | L2-4.3-Transparency-Disclosure-Framework-v1.md |
| Technical Documentation (EU AI Act Article 11) | Required if high-risk classification applies or is confirmed on review | P2-Worked-Example-Technical-Documentation-v1.md |

---

## 9. Open Assumptions — Items Requiring Validation

The following assumptions are embedded in this document and must be validated against real system data before this profile is used operationally.

| # | Assumption | Section | Validation Required From |
|---|---|---|---|
| A-001 | EU hosting confirmed; specific cloud provider not named | 3.4 | CTO / Head of Engineering |
| A-002 | Anthropic DPA in place; prompts not used for model training | 3.4 | Legal Counsel / CTO |
| A-003 | No fine-tuning applied to base model | 3.1 | Head of Engineering |
| A-004 | RAG corpus quarterly review cycle | 3.3 | Head of Product / Engineering |
| A-005 | Output labelling and UI disclaimer behaviour | 6 | Head of Product |
| A-006 | Audit trail logging per session | 6 | Head of Engineering |
| A-007 | EU AI Act classification confirmed as limited risk | 5.1 | Qualified German lawyer |
| A-008 | BRAK obligations assessed and addressed in product design | 5.2, 6 | Legal Counsel |

---

## 10. Document Notes

This system profile is the first Phase 2 worked example document. Subsequent Phase 2 documents will use this profile as their authoritative source for Vertrag.AI system characteristics. If any field in this profile is revised, all dependent documents should be reviewed for consistency.

**Dependent documents:**
- P2-Worked-Example-Risk-Classification-v1.md
- P2-Worked-Example-EU-AI-Act-Mapping-v1.md
- P2-Worked-Example-Technical-Documentation-v1.md
- P2-Worked-Example-Monitoring-Entry-v1.md
- P2-Reflection-Note-v1.md

---

*This document is a fictional worked example produced for educational and demonstration purposes. Vertrag.AI does not exist. All regulatory references are made in good faith for illustrative purposes and do not constitute legal advice. Professional legal review is required before any governance framework is applied operationally.*
