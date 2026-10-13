# China Regulatory Reporting Automation

End-to-end data pipeline architecture for financial regulatory compliance

> *Disclaimer: This repository contains no proprietary code or data. The institution is anonymised, and all diagrams are redrawn.*

---

## My Role

**2023–2024.** I owned this project end to end, from diagnosis to delivery. I diagnosed the problems in the legacy system, mapped the upstream data, and designed the 3+6 data model and the overall architecture. I also defined the regulatory and adjustment rules, built the 50+ Dataiku pipelines (ingestion, data quality, GL reconciliation, report generation, movement analysis, cross-validation), wrote the handover documentation and trained the business users who took over the system. The one exception was the physical database implementation of my data model in the bank's data warehouse, which the bank's technology team built.

---

## The Problem

Every major international bank operating in China faces the same regulatory data challenge: two regulators — NFRA and PBOC — with overlapping but inconsistent frameworks, hundreds of reports per submission cycle, and source data that was never designed with regulatory logic in mind.

The industry's default response has been to throw people at it. More headcount, more manual checks, more spreadsheet gymnastics. This works until it doesn't — and when it fails, it fails at 11pm before a submission deadline.

The deeper problem is structural. Most reporting systems in this space were never architected; they accumulated. Business data and regulatory logic live in the same tables. Validation is manual. Auditability is a fiction. Every change requires IT. Every error requires a person who knows where the bodies are buried.

When that person leaves, the system doesn't just slow down. It stops.

---

## The Solution

I independently architected and delivered a full automation suite from scratch — no dedicated engineering team, no external consultants, in three months. (The database implementation of the data model was built by the bank's technology team.)

![System Overview](assets/overview.png)

The core of the system is a custom **3+6 data model** that strictly separates business data from regulatory logic — so a change in one never breaks the other. On top of it, **50+ automation pipelines** handle ingestion, quality control, GL reconciliation, report generation, variance analysis, and cross-report validation end-to-end.

The design was built for longevity, not just delivery. Business users were trained to own and maintain the system independently. The documentation was written for handover, not for record-keeping. When I left, there was zero operational disruption.

The system outlived my time there. Then it outlived its platform. The methodology is still running.

**Built with:** `Dataiku` `SQL` `Confluence`

*Alteryx was the originally planned platform; the build was migrated to Dataiku before development began in earnest. Python was considered and deliberately not used (see [Q&A](ARCHITECTURE.md#6-qa)).*

→ [Architecture & Design Decisions](ARCHITECTURE.md)

---

## The Methodology

Delivery in three months wasn't the result of working faster. It was the result of thinking differently about what needed to exist at all.

The guiding principle — borrowed from aerospace, applied to banking — was to question every requirement before building anything, delete every process step that couldn't justify its existence, and automate only what remained. Most systems accumulate complexity because nobody asks whether the complexity was necessary in the first place.

The same principle drove the build-for-longevity decisions: low-code over Python, mirror tables over exception systems, deliberate denormalisation over theoretical purity. Every choice was evaluated against one question: can someone else maintain this without me?

→ [Philosophy: Sustainable Digitalisation](PHILOSOPHY.md)

---

## Outcomes

**Scope:** 900+ reports[^1] across NFRA and PBOC, covering 20+ branch entities.

| Metric | Result |
|---|---|
| Delivery timeline | 3 months |
| Monthly FTE saved | 3+ (net)[^2] |
| Reporting production time | 48 hours shorter[^3] |
| System complexity reduction | ~50% (estimate)[^4] |
| Validation | 100% pass rate on automated cross-report checks and GL reconciliation rules[^5] |
| Organisational impact | Adopted as bank-wide standard architecture |

[^1]: Report count = report templates × reporting entities (branches).
[^2]: Baseline: at least 6 full-time staff on the process. Net of my own ongoing maintenance time after go-live.
[^3]: Reporting production time per submission cycle, shortened by 48 hours.
[^4]: Estimate: a dozen-plus manually maintained spreadsheets replaced by 6 standardised configuration tables.
[^5]: Every production run must pass all automated cross-report consistency checks and GL reconciliation rules before submission.

The architecture was eventually adopted as the standard template for all future Finance regulatory reporting automation within the bank — extending beyond loans into a full cross-business framework. A long-standing reconciliation failure between NFRA 1104 and EAST reports was resolved as a byproduct of shared data lineage. When the low-code platform was later retired following a group-level platform decision, the engineering team didn't revert. They went looking for another tool to keep working the same way.


