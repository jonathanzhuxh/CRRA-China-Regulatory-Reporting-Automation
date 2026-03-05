# System Architecture & Design Decisions

## Context

This document covers the technical architecture of a regulatory reporting automation suite built for the Finance department of a top-tier international bank in China. The system processes 900+ reports across NFRA and PBOC frameworks, covering 20+ branch entities.

This is not a documentation of what was built. It is a record of why it was built this way.

## The Problem with the Previous System

The 1.0 system had three fundamental flaws:

No separation of concerns. Customer data, transaction data, and regulatory logic were entangled. A change in one place broke things in three others.

No elasticity. Field designs were rigid. Every regulatory update required IT intervention, code rewrites, and weeks of lead time.

No auditability. Calculations happened inside black boxes. When numbers were wrong, nobody could trace why.

These were not implementation problems. They were architecture problems. Fixing the implementation would have bought months. Redesigning the architecture bought years.

## The 3+6 Data Model

The core of the system is a two-layer data model that strictly separates what the data is from what the regulations require it to mean.

### Layer 1: Core Tables (本表)

Three tables form the source of truth:

**Corporate Customer Table** — One record per legal entity. Unique PK. Covers industry classification, enterprise scale, unified credit code, geography, country, and credit limits. Extensible via computed fields for special industry flags without touching the base structure.

**Corporate Loan Table** — Transaction-level granularity. One record per loan note, linked to the customer table via PK in a star schema. Covers institution, currency, principal, balance, interest rate, overdue metrics, five-tier classification, collateral type, and beneficiary.

**Retail Loan Table** — By design, no separate retail customer table exists. PII data for retail clients is collapsed into the transaction table itself, eliminating the attack surface for data leakage at the architectural level.

### Layer 2: Adjustment & Mapping Tables (调整表)

Six tables handle everything that deviates from the norm:

Three mirror adjustment tables — Structurally identical to their corresponding core tables, field for field. When upstream data has errors or regulatory logic requires overrides, business users write directly to these tables. No IT involvement, no code changes, no waiting.

Three special rule mapping tables:

∙ Special Industry Table — Maps industry codes to regulatory classifications that change frequently (digital economy, agricultural loans, etc.). Regulatory policy changes never touch the core tables.

∙ Special Customer Table — Handles edge cases for specific entity types with non-standard reporting requirements. Designed to self-retire as upstream data quality improves.

∙ Special Transaction Table — Isolates legacy system anomalies and non-standard product lines that cannot be classified through normal logic. Keeps the main pipeline clean.

### Key Architecture Decisions

**Why not full normalisation?**

Early design considered extracting collateral information into separate tables and splitting non-core fields into extension tables. This was rejected.

The reason was not laziness. It was pragmatism: full normalisation would have added months to delivery and significant ongoing complexity for marginal theoretical gain. The system needed to be in production before the reporting window closed. Deliberate denormalisation was the right call. It shipped on time.

**Why mirror tables instead of an exception handling system?**

A purpose-built exception system would have been technically cleaner. It would also have required IT to build and maintain it, and business users to learn a new interface.

Mirror tables are instantly understandable to anyone who knows the core tables. Business users can make batch corrections across multiple fields in a single operation. When upstream data fails at 11pm before a submission deadline, the mirror table is the difference between a crisis and a workaround.

**Why star schema for corporate loans?**

Customer attributes change infrequently. Loan transactions change constantly. Keeping them in separate tables with a clean PK relationship means customer updates propagate automatically without touching transaction records, and transaction queries don’t carry the weight of customer data they don’t need.

**Why collapse retail PII into the transaction table?**

A retail customer table would have been architecturally cleaner. It would also have created a centralised, queryable store of personal identity information — a liability that serves no operational purpose. The decision to denormalise PII into the transaction table was a deliberate risk reduction choice, not a shortcut.

## Processing Layer

Built on Dataiku — the first production deployment of the platform within Standard Chartered China, and the foundation of what became the bank’s low-code ecosystem.

*The migration story behind this

The original plan was to build on Alteryx, which several departments were already exploring. A group-level policy shift mandated a switch to Dataiku before development began in earnest. The migration happened in one month.

The approach was deliberate: first map every Alteryx concept to its Dataiku equivalent, step by step. Then explore what Dataiku could do differently. The constraint turned into an advantage — the forced re-examination of every assumption produced a cleaner implementation than the original plan would have.

This became the template for how other departments approached Dataiku. Training sessions started with a functional demo, followed by hands-on walkthroughs. No theoretical introductions, no slide decks about what low-code means. Show it working, then let people try it.

The result: Dataiku spread across Finance, Operations, Technology, and parts of the business-facing divisions. At peak, 800+ projects existed on the platform across Standard Chartered China. By code contribution volume, this project’s developer ranked first across the entire bank — by a significant margin.

When the platform was eventually discontinued, the bank didn’t abandon low-code. It went looking for a replacement.*

50+ pipeline components, organised into two modules:

### Core Control Module

**Data Ingestion** — The sole interface between the system and the central data warehouse (EDMP). All upstream data flows through a single entry point, ensuring every downstream component works from the same source. Current period and historical data are both managed here.

**Automated Quality Screening** — Triggered automatically on every data pull, bound directly to the ingestion action. No manual initiation required. Anomalies surface before any report generation begins — not after.

**General Ledger Reconciliation** — Financial totals from the data model are reconciled against the GL before submission. Catches discrepancies at the source rather than during regulatory review.

**Historical Data Store** — Hand-built repository for variance analysis. Regulatory reporting doesn’t just require current numbers — it requires explaining why numbers changed. The historical store makes this possible without relying on external archiving or manual snapshots. Each ingestion cycle automatically updates it.

**Supplementary Data Interface** — Analyses gaps in upstream data before report generation, reducing manual data entry to the irreducible minimum. The goal was always to eliminate manual entry entirely; this module tracks how close the system is to that goal.

### Regulatory Reporting Engine

**NFRA Components** — Core report generation across all 1104 framework templates, variance analysis against prior periods, cross-report validation, GL reconciliation, and historical archiving for audit and reuse.

**PBOC Components** — Core report generation, metadata export, automated rounding and zero-suppression adjustments (a PBOC-specific requirement), variance analysis, cross-report validation, GL reconciliation, and historical archiving.

**Regional Components** — Localised report generation for branch-specific regulatory requirements across 20+ entities. Same architecture, jurisdiction-specific logic.
All pipelines are chained via Dataiku Scenarios. One trigger initiates the entire sequence — ingestion, quality checks, calculations, validation, and output — without human coordination at any step.

### Transparency by Design

Every calculation in this system is visible, traceable, and auditable.

This was not an afterthought. The 1.0 system was a black box — when numbers were wrong, the only option was to call the person who built it. This system was designed so that any technically literate person can open a pipeline, follow the logic, and understand exactly how any output number was produced.

When the platform was eventually discontinued, this transparency was what allowed the engineering team to migrate without losing the logic. You cannot migrate a black box. You can migrate documented, visible calculations.

## Organisational Impact: When a Local Solution Becomes a Standard

A well-designed system doesn’t stay within its original boundaries.

The IT team responsible for the universal data model began adopting field designs from this architecture — a local financial model quietly becoming the reference point for the bank’s central 
data standard. The logical endpoint was always clear: if the universal model is designed correctly, the specialised model becomes unnecessary. That was the goal, not a compromise.

Operations teams began replicating the same automation patterns independently. The methodology spread without being mandated.

A long-standing reconciliation failure between NFRA 1104 and EAST reports — caused by inconsistent upstream sourcing — was resolved as a byproduct of shared data lineage. When the regulator later introduced a unified reporting framework combining both, the architecture was already aligned.

When the low-code platform was discontinued for political reasons, the engineering team didn’t revert. They went looking for another tool to keep working the same way.

***The system outlived its platform. The methodology outlived the system.***
