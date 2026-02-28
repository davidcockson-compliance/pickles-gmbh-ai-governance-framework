# Assumptions Log

**Project:** Pickles GmbH — AI Governance Framework
**Version:** v1
**Date:** 2026-02-28

---

## About This Document

This framework was built using a fictional company — Pickles GmbH — as the demonstration vehicle. Because no real company data was available during the build, every claim about Pickles GmbH's systems, operations, or characteristics is an assumption, not a verified fact.

This log records all of those assumptions in one place. Every document in the framework also flags its own assumptions inline using the marker `[ASSUMPTION]`.

**If you are adapting this framework for a real organisation:** this log is your starting point. Work through every assumption listed here and validate each one against your actual company data before treating any framework document as complete.

---

## Status Key

| Status | Meaning |
|---|---|
| 🔴 Unverified | Not confirmed against real data — placeholder only |
| 🟡 Partial | Partially confirmed — still needs full verification |
| 🟢 Confirmed | Verified against real company data |

---

## Company Profile Assumptions

| # | Assumption | Source Document | Status |
|---|---|---|---|
| A-001 | The company provides legal AI tools covering drafting, research, summarisation, and analysis | Framework outline | 🔴 Unverified |
| A-002 | Clients are German legal professionals or in-house legal departments | Framework outline | 🔴 Unverified |
| A-003 | The company operates under the EU AI Act, GDPR, and German professional confidentiality standards (BRAK) | Framework outline | 🔴 Unverified |
| A-004 | Third-party AI model providers may be in use | Framework outline | 🔴 Unverified |
| A-005 | Hosting location is EU-based | Framework outline | 🔴 Unverified |

---

## System-Level Assumptions (Phase 2 — Vertrag.AI)

These assumptions relate to the fictional Vertrag.AI system used in the Phase 2 worked example.

| # | Assumption | Source Document | Status |
|---|---|---|---|
| A-006 | EU hosting confirmed; specific cloud provider not named | P2-Worked-Example-System-Profile-v1.md | 🔴 Unverified |
| A-007 | Anthropic DPA in place; prompts not used for model training | P2-Worked-Example-System-Profile-v1.md | 🔴 Unverified |
| A-008 | No fine-tuning applied to base model | P2-Worked-Example-System-Profile-v1.md | 🔴 Unverified |
| A-009 | RAG corpus quarterly review cycle | P2-Worked-Example-System-Profile-v1.md | 🔴 Unverified |
| A-010 | Output labelling and UI disclaimer behaviour as described | P2-Worked-Example-System-Profile-v1.md | 🔴 Unverified |
| A-011 | Audit trail logging per session | P2-Worked-Example-System-Profile-v1.md | 🔴 Unverified |
| A-012 | EU AI Act classification confirmed as limited risk | P2-Worked-Example-System-Profile-v1.md | 🔴 Unverified — requires qualified lawyer review |
| A-013 | BRAK obligations assessed and addressed in product design | P2-Worked-Example-System-Profile-v1.md | 🔴 Unverified |

---

## How to Resolve Assumptions

For each assumption, the validation process requires:

1. Identifying the relevant data source (CTO, Head of Engineering, Legal Counsel, etc.)
2. Obtaining written confirmation of the actual position
3. Updating the relevant framework document to replace the assumed value with the confirmed value
4. Removing the `[ASSUMPTION]` flag from that field
5. Updating this log with status 🟢 Confirmed and the date confirmed

Some assumptions (particularly A-012 regarding EU AI Act risk classification) require review by a qualified lawyer, not just internal verification.

---

## Resolved Assumptions

*None — this framework was built entirely on fictional company data. All assumptions remain unverified. Confirm against real company data before operational use.*

---

*Last updated: 2026-02-28. This log should be maintained and updated whenever the framework is adapted for a real organisation.*
