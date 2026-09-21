# CHINT — System Landscape

*Extracted from the 2026 Marketo Vendor RFP.*

## Core Systems

| System | Role | Status |
|--------|------|--------|
| **Marketo** | Marketing automation platform — lead capture, nurture, scoring, distribution | Deployed since 2023; 22 countries live |
| **Microsoft Dynamics CRM** | Customer relationship management | Technically integrated with Marketo, but most countries not yet enabled; sales only use at quotation stage |
| **Email Platform** | Email delivery | Connected to Marketo |
| **飞书 (Feishu/Lark)** | Dashboard and reporting | Dashboards built on Feishu; under strain as lead volume grows |

## Integration Flow

```
Email Platform ←→ Marketo ←→ Microsoft Dynamics CRM ←→ 飞书 Dashboard
                     ↓
            Social Media Platforms
         (third-party — integration TBD)
```

## Integration Status

- **Email Platform ↔ Marketo ↔ Microsoft Dynamics CRM ↔ 飞书 Dashboard:** Connected; requires monthly monitoring, troubleshooting (network issues, API exceptions, field mapping), and bi-directional data transfer assurance
- **Marketo ↔ Social Media Platforms:** Integration support requested — not yet built
- **Microsoft Dynamics CRM:** Technically connected but under-utilised — most countries not enabled, sales only interact at quotation stage

## Current Pain Points

- **Bi-directional sync troubleshooting is difficult** across systems
- **Data inconsistency:** subsidiaries upload data without unified field standards; garbled characters in non-Latin languages
- **Feishu dashboards** are straining as lead volume grows
- **Data compliance** concerns unaddressed

## Templates & Content Layer

| Asset | Notes |
|-------|-------|
| Newsletter templates | Multi-device adaptation needed; display anomalies to fix |
| Landing page templates | Multi-device adaptation needed |
| Form templates | Lack business-tiering logic — not differentiated by product line or marketing stage |
| Training PPTs, Guidelines, FAQs, SOPs | Standard documents to maintain and update based on feedback |

## Customer Data

| Dimension | Status |
|-----------|--------|
| Lead volume | 100k leads (license basis) |
| Customer tagging system | Immature — lacking multi-dimensional integration (source, behaviour, industry, interest) |
| 360° customer profile | Not yet achieved — target state |
| Lead scoring model | Initial version exists but subjective; lacks data-driven validation and behavioural scoring balance |

---

*Source: `../genoptima/2026-marketo-rfp-chint-en.md`*
