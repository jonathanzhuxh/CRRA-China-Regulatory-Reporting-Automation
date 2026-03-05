# China Regulatory Reporting Automation


End-to-end data pipeline architecture for financial regulatory compliance

## The Problem

A top-tier international bank in China faced a breaking point: 900+ regulatory reports across NFRA and PBOC frameworks, all dependent on manual processing, with data inconsistencies, high compliance risks, and submission windows being routinely missed.

The existing system had no real architecture — no separation between business data and regulatory logic, no validation, no auditability. Every change required IT intervention. Every error required manual firefighting.

## The Solution

Independently architected and delivered a full automation suite from scratch — no dedicated engineering team, no external consultants, in three months.

Core components:

1. A custom 3+6 data model decoupling core business data from regulatory logic

2. 50+ automation pipelines built on Dataiku covering ingestion, calculation, validation, and variance analysis

3. Automated anomaly detection and cross-report reconciliation

4. Confluence-based documentation enabling full handover to business users

![System Overview](assets/overview.png)

## Engineering Philosophy: The Five-Step Path

Borrowed from aerospace, proven in banking.

In 2021, during a walkthrough of SpaceX’s Starbase facility, Musk outlined the engineering philosophy behind how his teams build — five steps, in strict order:

**1. Make the requirements less dumb.**
	
**2. Delete the part or process step.**
	
**3. Simplify or optimize.**
	
**4. Accelerate cycle time.**
	
**5. Automate.**

*A note on testing: Musk applies one additional principle across steps 3–5 — test the full system, not just the parts. SpaceX didn’t just test rocket components. They launched, and accepted the explosion as data. The only test that matters is the one that replicates real conditions at full scale.*

It was a casual conversation, not a management framework. Most people who heard it filed it under “interesting Musk anecdote.”

I filed it under “this is exactly what’s wrong with how banks build things.”

The result: three months from blank page to production.

## Design Philosophy: Building for Longevity

Delivery was never the finish line. The real measure of success was what happened after handover.

This system was designed across three layers of sustainability:

**System** — Decoupled architecture ensures regulatory logic changes never touch core business data. No black boxes. Every calculation is traceable and maintainable by the next person.

**People** — Business users were trained to own and maintain the system independently. The goal was to eliminate IT dependency, not transfer it.

**Organisation** — The architecture and methodology were adopted as the standard template for all future Finance regulatory reporting automation within the bank — extending beyond loans into a full cross-business framework.

***Sustainable digitalisation means building something that outlives its creator.***

## Architecture Philosophy

Five principles, in order:

**Decoupling** — Business data and regulatory logic are strictly separated. Changes in one never break the other.

**Minimalism** — Every component earns its place. Nothing exists without a purpose. No redundancy, no padding.

**Scalability** — Because the system is minimal and decoupled, it scales without accumulating debt. What started as a loans reporting architecture became the Finance department’s organisation-wide automation standard.

**Transparency** — No black boxes. Every calculation is visible, traceable, and auditable — by design, not by documentation.

**Pragmatism** — Perfect is the enemy of shipped. Where extreme normalisation would have delayed delivery, deliberate denormalisation was chosen. The system went live; the theoretical purity did not.

## Outcomes

|Metric                      |Result                                    |
|----------------------------|------------------------------------------|
|Delivery timeline           |3 months                                  |
|Monthly FTE saved           |3+                                        |
|Report delivery acceleration|48 hours                                  |
|System complexity reduction |40%                                       |
|Data consistency            |100% via automated validation             |
|Organisational impact       |Adopted as bank-wide standard architecture|

## Tech Stack
`Dataiku` `SQL` `Python` `Alteryx` `Confluence`

→ [System Architecture & Design Decisions](ARCHITECTURE.md)

