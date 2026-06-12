# Pickles GmbH — AI Governance Framework

<p class="dc-sub">An open-source AI governance framework for German legal AI providers. Built for <strong>Pickles GmbH</strong>, a fictional German legal-tech company whose product, <strong>Vertrag.AI</strong>, is an AI contract review tool — and walked through the complete framework end to end.</p>

<span class="dc-pill">EU AI Act</span><span class="dc-pill">GDPR</span><span class="dc-pill">BDSG</span><span class="dc-pill">BRAK professional standards</span><span class="dc-pill">CC BY 4.0</span>

!!! warning "Framework proposal — not a certification"

    This framework is an educational resource and demonstration piece. It is
    **not a legal compliance certification**, and qualified legal review is
    required before any operational use. Every unverified assumption is
    flagged inline and logged. Read the [Disclaimer](DISCLAIMER.md) and the
    [Assumptions Log](ASSUMPTIONS-LOG.md) before use.

[Start with Stage 1](stage-1-regulatory-orientation/STAGE1-Regulatory-Orientation-Note-v1.md){ .md-button .md-button--primary }
[Worked example](phase-2-worked-example/P2-Worked-Example-System-Profile-v1.md){ .md-button }

---

## Why This Exists

There weren't clear worked examples of what EU AI Act compliance documentation looks like in practice for a legal AI company. Rather than write documents manually, I designed a multi-agent system to produce them — with regulatory research, assumption tracking, and quality controls built into the generation process.

The result is 22 documents across five stages, a worked example showing a fictional contract review tool walked through the complete framework, and a reusable methodology that other organisations can adapt.

---

## Framework Structure

<div class="grid cards" markdown>

-   :material-compass-outline: **Stage 1 — Regulatory Orientation**

    ---

    Situates Vertrag.AI within EU and German law: EU AI Act, GDPR, BDSG,
    and BRAK professional standards.

    [:octicons-arrow-right-24: Orientation Note](stage-1-regulatory-orientation/STAGE1-Regulatory-Orientation-Note-v1.md)

-   :material-office-building-cog-outline: **Stage 2 — Governance Foundation**

    ---

    AI system inventory, risk classification framework, intake and approval
    workflow, and human oversight policy.

    [:octicons-arrow-right-24: AI System Inventory](stage-2-governance-foundation/L1-3.1-AI-System-Inventory-v1.md)

-   :material-scale-balance: **Stage 3 — Regulatory Alignment**

    ---

    EU AI Act risk mapping, Article 11 technical documentation template,
    transparency framework, data flow map, DPIA, and vendor/model risk.

    [:octicons-arrow-right-24: EU AI Act Risk Mapping](stage-3-regulatory-alignment/L2-4.1-EU-AI-Act-Risk-Mapping-Matrix-v1.md)

-   :material-monitor-eye: **Stage 4 — Monitoring & Controls**

    ---

    AI monitoring framework, incident response playbook, and model change
    management protocol.

    [:octicons-arrow-right-24: Monitoring Framework](stage-4-monitoring-controls/L3-6.1-AI-Monitoring-Framework-v1.md)

-   :material-handshake-outline: **Stage 5 — Commercial Packaging**

    ---

    Client-facing governance information pack and enterprise sales
    enablement kit.

    [:octicons-arrow-right-24: Governance Information Pack](stage-5-commercial-packaging/L4-7.1-AI-Governance-Information-Pack-v1.md)

-   :material-test-tube: **Phase 2 — Worked Example**

    ---

    Vertrag.AI walked through the complete framework: system profile, risk
    classification, EU AI Act mapping, technical documentation, monitoring
    entry, and a reflection note.

    [:octicons-arrow-right-24: System Profile](phase-2-worked-example/P2-Worked-Example-System-Profile-v1.md)

</div>

---

## Worked Example — Vertrag.AI

Phase 2 takes a fictional contract review tool, Vertrag.AI, through the complete framework end to end. Every key template is populated with realistic content, and the risk classification reasoning is made explicit at each decision gate.

The worked example demonstrates:

- How the risk classification decision tree produces traceable, defensible outputs
- Why the EU Act classification (limited risk) and the internal classification (Medium-High) diverge, and why that gap matters
- What the human oversight gate looks like in a professional-liability context
- How the monitoring framework handles legally privileged material

See the [System Profile](phase-2-worked-example/P2-Worked-Example-System-Profile-v1.md) and the [Reflection Note](phase-2-worked-example/P2-Reflection-Note-v1.md) for the full worked example and a first-person account of what the exercise revealed about the framework's design.

---

## Methodology

The framework was produced by a multi-agent Claude Code system with five defined agent roles: Orchestrator, Research Reader, Document Drafter, Assumptions Tracker, and Run Summariser. The system runs autonomously from regulatory source documents placed in an input folder, producing audit-ready Markdown documentation with explicit assumption flagging throughout.

The documents are the output. The system design is the methodology.

The next stage is testing whether this approach transfers to a different jurisdiction and regulatory architecture.

**Estimated build cost for Phase 1 (16 documents):** $4–10 USD using Claude Sonnet with prompt caching.

---

## Regulatory Coverage

| Regulation | Coverage |
|---|---|
| EU AI Act (Regulation (EU) 2024/1689) | Risk classification, Article 50 transparency obligations, Annex III mapping, Article 11 technical documentation structure |
| GDPR (Regulation (EU) 2016/679) | Data flow mapping, DPIA, sub-processor obligations, data subject rights |
| BDSG (Bundesdatenschutzgesetz) | German national data protection overlay |
| BRAK professional standards | Lawyer obligations when using AI tools, client confidentiality |

---

## Using This Framework

This framework is designed to be adapted, not copied verbatim. Before operational use:

1. Replace all fictional Pickles GmbH / Vertrag.AI content with your actual system data
2. Resolve all `[ASSUMPTION]` flags against real company information
3. Have the framework reviewed by a qualified lawyer in your jurisdiction
4. Update regulatory references if the EU AI Act or related guidance has been updated since this was produced

The [Assumptions Log](ASSUMPTIONS-LOG.md) lists every unverified assumption across the framework. Start there.

---

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — you are free to use, adapt, and distribute this framework, including commercially, provided you give appropriate credit.

---

## Author

Built by [David Cockson](https://davidcockson.com) — compliance and governance professional with a background in financial services and igaming RegTech.

*Pickles GmbH does not exist. All company characteristics, systems, and scenarios in this framework are fictional and produced for educational and demonstration purposes only.*

---

## Related

- [Sable AI Ltd AI Governance Framework](https://github.com/davidcockson-compliance/sable-ai-governance-framework) — UK jurisdiction equivalent covering UK GDPR, Data (Use and Access) Act 2025, Equality Act 2010, and ICO AI in Recruitment guidance. Built for a fictional UK HR/recruitment AI startup.
