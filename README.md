Regulatory Reporting Automation Suite
End-to-end data pipeline architecture for financial regulatory compliance

The Problem
A top-tier international bank in China faced a breaking point: 900+ regulatory reports across NFRA and PBOC frameworks, all dependent on manual processing, with data inconsistencies, high compliance risks, and submission windows being routinely missed.
The existing system had no real architecture — no separation between business data and regulatory logic, no validation, no auditability. Every change required IT intervention. Every error required manual firefighting.

The Solution
Independently architected and delivered a full automation suite from scratch — no dedicated engineering team, no external consultants, in three months.

Core components:
	∙	A custom 3+6 data model decoupling core business data from regulatory logic
	∙	50+ automation pipelines built on Dataiku covering ingestion, calculation, validation, and variance analysis
	∙	Automated anomaly detection and cross-report reconciliation
	∙	Confluence-based documentation enabling full handover to business users

Engineering Philosophy: The Five-Step Path
Borrowed from aerospace, proven in banking.
1. Challenge every requirement
Banks are fertile ground for fake requirements — bureaucratic habits, legacy workarounds, and “we’ve always done it this way” logic. Before building anything, every requirement was interrogated. Many didn’t survive the question: does this actually need to exist?
2. Delete ruthlessly
The best component is no component. The best manual adjustment is no manual adjustment — fix the source, don’t patch the symptom. This project eliminated entire process layers that had existed for years simply because no one had questioned them.
3. Test at full scale, with real data
Unit tests and standard UAT don’t catch production problems. Time pressure plus real data plus edge cases is what breaks systems. The only way to know if something works is to run it as if it’s already live.
4. Simplify what remains
Regulatory reporting has a natural gravity towards complexity. Resist it. A system that can’t be understood in one sitting can’t be maintained in production. Simplicity is not a compromise — it is the only path to long-term stability.
5. Then automate — and iterate fast
Automation locks in everything above. When something breaks in production, fast iteration beats perfect planning. Ship the fix, don’t schedule a meeting about the fix.
The result: three months from blank page to production.

Design Philosophy: Building for Longevity
Delivery was never the finish line. The real measure of success was what happened after handover.
This system was designed across three layers of sustainability:
System — Decoupled architecture ensures regulatory logic changes never touch core business data. No black boxes. Every calculation is traceable and maintainable by the next person.
People — Business users were trained to own and maintain the system independently. The goal was to eliminate IT dependency, not transfer it.
Organisation — The architecture and methodology were adopted as the standard template for all future Finance regulatory reporting automation within the bank — extending beyond loans into a full cross-business framework.
Sustainable digitalisation means building something that outlives its creator.

Architecture Philosophy
Five principles, in order:
Decoupling — Business data and regulatory logic are strictly separated. Changes in one never break the other.
Minimalism — Every component earns its place. Nothing exists without a purpose. No redundancy, no padding.
Scalability — Because the system is minimal and decoupled, it scales without accumulating debt. What started as a loans reporting architecture became the Finance department’s organisation-wide automation standard.
Transparency — No black boxes. Every calculation is visible, traceable, and auditable — by design, not by documentation.
Pragmatism — Perfect is the enemy of shipped. Where extreme normalisation would have delayed delivery, deliberate denormalisation was chosen. The system went live; the theoretical purity did not.

Outcomes

|Metric                      |Result                                    |
|----------------------------|------------------------------------------|
|Delivery timeline           |3 months                                  |
|Monthly FTE saved           |3+                                        |
|Report delivery acceleration|48 hours                                  |
|System complexity reduction |40%                                       |
|Data consistency            |100% via automated validation             |
|Organisational impact       |Adopted as bank-wide standard architecture|

Tech Stack
Dataiku SQL Python Alteryx Confluence

→ System Architecture & Design Decisions
