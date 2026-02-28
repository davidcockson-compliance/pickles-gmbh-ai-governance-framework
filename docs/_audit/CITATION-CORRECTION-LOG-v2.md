# Citation and Operator Analysis Correction Log — v2

**Date:** 2026-02-28
**Scope:** EU AI Act article numbering and operator role corrections across phase 2 worked example documents and homepage
**Reference:** Regulation (EU) 2024/1689 (OJ L, 2024/1689, 12.7.2024)
**Source text verified via:** `_input/stage-3-regulatory-extracts.md` (extracted from `_input/_raw-sources/EU-AI-Act-full-text.txt`)

---

## Sub-Article Mapping Applied

The task brief's mapping table had 52(3)→50(2) and 52(4)→50(4), which was inconsistent with the actual Article 50 source text. Corrections were applied using content-based mapping verified against the regulatory extract:

| Draft article (wrong) | Final article (correct) | Subject | Basis |
|---|---|---|---|
| Article 52(1) | Article 50(1) | AI system interaction disclosure — chatbot | Provider obligation; applies where AI nature not obvious from context |
| Article 52(2) | Article 50(3) | Emotion recognition / biometric categorisation | Deployer obligation |
| Article 52(3) | Article 50(4) | Synthetic content / deep fake disclosure | Deployer obligation; phase 2 docs used 52(3) for deployer disclosure |
| Article 52(4) | Article 50(2) | Machine-readable marking of AI-generated outputs | Provider obligation; phase 2 docs used 52(4) for machine-readable marking |

> **Note on task brief mapping discrepancy:** The task brief listed 52(3)→50(2) and 52(4)→50(4), with descriptions swapped relative to the source text. Article 50(2) in the final regulation requires machine-readable *marking* (provider obligation); Article 50(4) requires *disclosure* of deep fakes (deployer obligation). The content of 52(3) in phase 2 documents was deployer disclosure (→50(4)) and 52(4) was machine-readable marking (→50(2)). Content-based mapping was applied per the task instruction to "check the content of each sub-article reference against the mapping table." [Legal review recommended to confirm.]

---

## Defects Addressed

| ID | Defect | Files Changed | Changes Made | Status |
|---|---|---|---|---|
| DEFECT-001 | Homepage Article 52 → Article 50 | `README.md` | Regulatory Coverage table: `Article 52 transparency obligations` → `Article 50 transparency obligations` | Complete |
| DEFECT-002 | Phase 2 Article 52 numbering throughout | `P2-Worked-Example-EU-AI-Act-Mapping-v1.md`, `P2-Worked-Example-Risk-Classification-v1.md`, `P2-Worked-Example-System-Profile-v1.md`, `P2-Worked-Example-Technical-Documentation-v1.md`, `P2-Reflection-Note-v1.md` | All Article 52 transparency references replaced with Article 50 using content-based sub-article mapping. Section headings, table cells, gate descriptions, GAP analysis, review triggers, and classification summary boxes updated. ~35 instances corrected across 5 files. | Complete |
| DEFECT-003 | Article 50 mislabelled as EU database registration | `P2-Worked-Example-EU-AI-Act-Mapping-v1.md` | Non-applicable provisions table row: `Article 50 — Registration in EU database (provider)` → `Article 49 — Registration in the EU database referred to in Article 71 (provider)`. Reason column updated to identify Article 49 and Article 71 correctly. Existing correct Article 49 reference in conditional note left unchanged. | Complete |
| DEFECT-004 | Pickles GmbH operator role: deployer → provider | `P2-Worked-Example-EU-AI-Act-Mapping-v1.md`, `P2-Worked-Example-Risk-Classification-v1.md`, `P2-Worked-Example-System-Profile-v1.md` | Classification tables updated: Pickles GmbH now identified as Provider of Vertrag.AI (Article 3(3)). Law firm customer row added (Deployer, Article 3(4)). Anthropic row updated to include Articles 51–55. Gate 3 clarification note added explaining layered GPAI/product structure. Section 2.1 General Provisions updated with Article 3(3) provider row and corrected Article 3(4) deployer row. Section 2.4 reframed: Article 26 correctly identified as law firm deployer obligations; Pickles GmbH role recharacterised as provider enabling deployer compliance. | Complete |
| DEFECT-005 | Article 16 section mislabelled as deployer obligations | `P2-Worked-Example-EU-AI-Act-Mapping-v1.md` | Section 2.3 renamed from `Deployer Obligations (Article 16 applied proportionately)` to `Provider Obligations Applied Voluntarily (Article 16 — Good Practice at Limited-Risk Tier)`. Section intro updated to correctly identify Pickles GmbH as provider applying Article 16 voluntarily. Transparency-to-deployers row updated to reflect provider's role in providing instructions for use. | Complete |
| DEFECT-006 | Article 50(1) chatbot reasoning legally weak | `P2-Worked-Example-EU-AI-Act-Mapping-v1.md`, `P2-Worked-Example-Risk-Classification-v1.md` | Article 50(1) obligation row rewritten: removed incorrect premise ("lawyers are not natural persons"); replaced with correct legal test (AI nature obvious from context to a reasonably informed professional user). Status updated from "Not applicable to standard use case" to "Low risk — AI nature likely obvious from context; assess per interface." Monitor note updated to flag per-interface assessment requirement. | Complete |
| DEFECT-007 | Stage 1 Orientation Note terminology | `_output/stage-1-regulatory-orientation/STAGE1-Regulatory-Orientation-Note-v1.md` | Section 5.5 header changed from "transparency obligations for operators" to "transparency obligations for providers and deployers." Clarifying note added distinguishing Article 50(1)–(2) as provider obligations and Article 50(3)–(4) as deployer obligations. Article 50(1) description updated to "where not otherwise obvious from context." | Complete |

---

## Secondary Audit Results

| File | Article 52 transparency references | Status |
|---|---|---|
| `_output/stage-3-regulatory-alignment/L2-4.3-Transparency-Disclosure-Framework-v1.md` | None found — uses Article 50 throughout, with correct sub-article references | ✅ No changes required |
| `_output/stage-5-commercial-packaging/L4-7.1-AI-Governance-Information-Pack-v1.md` | None found — uses Article 50 correctly | ✅ No changes required |
| `_output/stage-5-commercial-packaging/L4-7.2-Enterprise-Sales-Enablement-Kit-v1.md` | None found — uses Article 50 correctly | ✅ No changes required |
| `phase-2-worked-example/P2-Worked-Example-Monitoring-Entry-v1.md` | None found in grep results | ✅ No changes required |
| `ASSUMPTIONS-LOG-internal-v1.md` | A-006 had `Article 52 disclosure obligations` — corrected to `Article 50` | ✅ Corrected |

**Historical records not modified (correct to reference old errors):**
- `CITATION-AUDIT-LOG.md` — preserves pre-correction error record
- `CITATION-AUDIT-LOG-v2.md` — post-correction record from prior session
- `_audit/CITATION-CORRECTION-LOG-article-50-52.md` — prior audit report

---

## Quality Check

- [x] All seven defects addressed and logged
- [x] No Article 52 transparency references remain in any framework output or phase 2 document
- [x] No instance of Article 16 described as deployer obligations in primary documents
- [x] No instance of Article 50 described as registration (DEFECT-003 corrected to Article 49)
- [x] Pickles GmbH correctly identified as provider of Vertrag.AI (Article 3(3)) in all Phase 2 documents
- [x] Law firm customers correctly identified as deployers of Vertrag.AI (Article 3(4))
- [x] Article 26 obligations reframed as applying to law firm deployers; Pickles GmbH role as enabler of deployer compliance documented
- [x] Article 50(1) rationale updated to correct legal test (obvious from context; not "lawyers aren't natural persons")
- [x] Correction log written to `_audit/`

---

## Remaining Items Flagged for Legal Review

1. **Sub-article mapping 52(3)/(4) vs 50(2)/(4):** The task brief had these mapped as 52(3)→50(2) and 52(4)→50(4); corrections applied as 52(3)→50(4) and 52(4)→50(2) based on source text content. A qualified lawyer should confirm the content-based mapping is correct before the framework is treated as citation-clean.

2. **Article 50(1) chatbot disclosure — "obvious from context" standard:** The updated rationale now correctly applies the legal test. However, whether the AI nature of Vertrag.AI is sufficiently obvious to satisfy Article 50(1) in the professional B2B context requires legal opinion. This is flagged in the document as requiring interface-by-interface assessment.

3. **Article 50(4) safe harbour — "human review or editorial control":** Whether the mandatory lawyer review gate in Vertrag.AI constitutes editorial control sufficient for the Article 50(4) safe harbour remains unresolved. Legal review of the disclosure form is required (flagged in GAP-002).

4. **Article 50(2) machine-readable marking — DOCX format feasibility:** GAP-001 (machine-readable labelling in DOCX output) remains an open gap. No technical solution has been assessed. Legal view required on scope of obligation for document-based output.

5. **Article 26 obligations reframing:** The restructured Section 2.4 now identifies Article 26 obligations as belonging to law firm deployers, with Pickles GmbH's role being to enable deployer compliance. This reframing has not been reviewed by a lawyer and may require adjustment once Pickles GmbH's exact contractual and operational relationships with law firm clients are confirmed.

---

*This log records corrections to citation accuracy and legal characterisation only. No substantive governance design changes were made. Professional legal review remains required before any document is relied upon operationally.*
