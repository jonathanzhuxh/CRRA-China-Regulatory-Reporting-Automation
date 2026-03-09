## Chapter 1 — Musk的五步法在银行 (Applying Musk's Five-Step Engineering Process to Bank Regulatory Reporting)

Banks and Elon Musk's engineering philosophy seem like they belong in different universes.

One moves in decades. The other moves in weeks. One optimises for never being wrong. The other optimises for finding out what's wrong as fast as possible.

And yet: in 2022, I used the Five-Step Engineering Process to rebuild a regulatory reporting system covering 900+ reports across China's two main financial regulators — and delivered it in three months.

In 2021, during a walkthrough of SpaceX's Starbase facility, Musk outlined the philosophy behind how his teams build — five steps, in strict order:

**1. Make the requirements less dumb.**
**2. Delete the part or process step.**
**3. Simplify or optimise.**
**4. Accelerate cycle time.**
**5. Automate.**

*One additional principle runs across steps 3–5: test the full system, not just the parts. SpaceX didn't just test rocket components. They launched, and accepted the explosion as data.*

It was a casual conversation, not a management framework. Most people filed it under "interesting Musk anecdote." I filed it under "this is exactly what's wrong with how banks build things."

The instinct in financial services is to skip straight to step five. Requirements are handed down, processes are assumed, complexity accumulates — and then someone decides to automate it. What you get is a faster version of the wrong thing.

### Step 1: Make the requirements less dumb

In banks, requirements accumulate like sediment. A process exists because someone added it five years ago to solve a problem that no longer exists. Nobody removed it because nobody questioned it.

Early in this project, a senior stakeholder asked for a trigger to regenerate a single branch's reports independently. The request came from a genuine fear: what if one branch has a problem? But the answer to that fear wasn't a selective rerun trigger — it was better data quality upstream. Allowing selective reruns would have introduced exactly the data inconsistency the system was built to eliminate.

I pushed back. The trigger was never built. Six months later, nobody asked about it again.

**The lesson: most requirements are answers to fears, not solutions to problems. Find the fear first.**

### Step 2: Delete the part or process step

The original system had over a dozen manual maintenance spreadsheets — each a workaround for a different data quality problem, each a single point of failure.

I replaced them with six standardised configuration tables. Not because six is better than twelve — but because most of those spreadsheets existed to compensate for problems fixable upstream, or edge cases that had stopped occurring, or logic made redundant by changes nobody had tracked.

**The lesson: workarounds accumulate faster than problems get solved. Deletion requires courage, not just analysis.**

### Step 3: Simplify or optimise

The core of this system is a 3+6 data model: three tables for business data, six for regulatory logic. The two layers never touch directly. When regulators changed requirements, changes stayed in the adjustment tables. Core data was never touched. No IT involvement, no code changes, no waiting.

**The lesson: simplification isn't subtraction. Done right, it's multiplication.**

### Step 4: Accelerate cycle time

Accelerating cycle time isn't about moving faster. It's about finding out what's wrong sooner.

Run the entire pipeline with actual production data, under actual deadline pressure, and see what breaks. Every major issue in this system was found this way. The cycle compressed every time — not because the system got luckier, but because each failure made the next fix faster.

**The lesson: shorten the distance between "something is wrong" and "it's fixed." Everything else follows.**

### Step 5: Automate

Automation is the last step, not the first. Automate a flawed process and you get a faster flawed process. Automate a simplified, tested, clean process and you get something that compounds.

By the sixth month, the team had stopped thinking about it as a system they were managing and started thinking about it as infrastructure. That's the goal.

**The lesson: automate to lock in everything you've already fixed. Success is when nobody has to think about it anymore.**

### Epilogue

Three months after I started, the system went live. Two years later, the platform it was built on was discontinued — a group-level policy decision, nothing to do with performance.

The engineering team didn't revert to manual processes. They went looking for another tool to keep working the same way.

*The system outlived its platform. The methodology outlived the system.*

That's the real test of an engineering philosophy: not whether it delivers on time, but whether it changes how the people around it think about problems.

---

## Chapter 2 — 可持续的数字化 (Sustainable Digitalisation)

It didn't start as a philosophy. It started as a fear.

At JPMorgan, I inherited a regulatory reporting process with no documentation and no institutional memory. The person before me was gone. The logic lived nowhere except in the system itself — and the system didn't explain itself.

I spent months reverse-engineering what should have taken days. Eventually I built a solution. Then a new problem surfaced: what happens when I leave?

That question changed how I thought about building things. *Whatever I build, it cannot depend on me to survive.*

### Three levels of sustainability

**Level 1 — System.** No black boxes. Every calculation visible, every logic traceable. A system that depends on its creator's memory is not a system — it's a liability. When the platform was discontinued, the team could migrate because the logic was visible. You cannot migrate a black box.

**Level 2 — People.** Transfer knowledge deliberately and completely. Train the team not just to use the system, but to own it. The goal is to make your continued involvement unnecessary — not to make yourself the guardian of institutional knowledge. A system that only runs because you're watching it isn't a system. It's a dependency.

**Level 3 — Organisation.** Design for impact beyond your own tenure. The architecture became the standard template for all future Finance automation across the bank — extending beyond the original scope, spreading without being mandated, outlasting the people and platforms that created it.

### The counterintuitive truth

The most durable form of job security is building things that don't need you.

Not because it makes you dispensable — but because it frees you to keep moving. Every system you build that runs without you is proof that your value is in the thinking, not the doing. And thinking, unlike doing, compounds.

*I left. The system kept running.*

---

## Chapter 3 — 自动化不是结束，而是开始 (Automation Is Not the Finish Line)

There is a belief, widespread in financial services, that automation is the destination.

Get the system built, get it live, get it signed off — and the work is done. This belief is understandable. It is also wrong. And in regulated environments, it is expensively wrong.

**Automation is not the finish line. It is the beginning of a long, ongoing operational commitment.**

### What a live system actually demands

After the system I built at Standard Chartered went live, my work didn't reduce. It changed.

Every month, I spent five to six days on operations alone — monitoring actual submission runs, tracing anomalies, validating that outputs matched regulatory expectations under real conditions. On top of that, I was making incremental upgrades every single month: tightening logic, closing edge cases, extending coverage as the business evolved.

Then there was the upstream work. The system's long-term quality depended on the quality of the data feeding it. A significant part of my time went toward mapping and improving upstream data sources — because a cleaner upstream meant a simpler, more reliable downstream. That work was unglamorous and invisible, but it was what made the system progressively better rather than progressively more patched.

None of this was unusual or unexpected. It was simply what owning a live regulatory reporting system requires.

The confusion — and it is a confusion, not a deliberate choice — arises when organisations treat two very different things as equivalent: a system that no longer depends on its original creator, and a function that no longer needs to exist at all. The first is a design objective. The second is a category error.

### The cognitive error non-technical leaders make

I've seen this pattern repeatedly, and I don't think it comes from bad faith. It comes from a fundamental misunderstanding of what automation is.

To a non-technical leader, a system that runs automatically looks like a problem that has been solved. The manual work is gone. The spreadsheets are gone. The overnight reconciliation panic is gone. Therefore: the person who built it is no longer needed.

What this misses is everything that keeps a live system running well.

Regulatory requirements in China don't update on a fixed schedule. In 2025 alone, there were two significant off-cycle framework updates — the kind that arrive without warning and require immediate response. I had anticipated one of them from early in the year, based on my reading of the macro environment, and had already built ahead for it. The architecture absorbed the change cleanly, without crisis.

That anticipation is not a technical skill. It is the accumulated product of sustained attention — to the regulatory environment, to the data landscape, to the signals that indicate where policy is heading before the announcements arrive. It accrues to whoever holds the function continuously. It does not transfer in a handover document. And no tool, however capable, generates it independently.

When that function is eliminated at project completion, what stops is not just a person. It is a trajectory — the incremental improvements, the upstream work without a ticket number, the judgment that was still being built. The system was designed not to need its creator. It was not designed to run without anyone.

### The question most organisations don't ask

Most institutions calculate the cost of building. They don't calculate the cost of owning.

The project budget covers delivery: UAT, signoff, go-live, celebration. It almost never covers the operational reality that follows — the maintenance cycles, the regulatory update responses, the upstream data work, the judgment calls that don't fit in a ticket.

This is a structural problem, not an individual one. The people making the build decision are rarely the people who will live with the operational consequences. Delivery is visible and time-bounded. Operational drag is invisible and open-ended. The incentives point in the wrong direction.

The result is predictable. A system gets built, celebrated, and handed over. A year later, it's struggling to keep pace with regulatory changes. Two years later, the original team has dispersed and the edge cases are mysteries. Three years later, the conversation turns to rebuilding.

The cycle repeats — not because the original build was poor, but because the organisation never committed to what a live system actually requires.

### What sustainable automation actually requires

A system in production is not a completed project. It is a living commitment.

It will need monthly attention, not annual reviews. It will need someone who understands not just the logic, but the context — the regulatory environment, the upstream data landscape, the business changes that will eventually require architectural responses.

It will need to be audited. When a regulator asks how a number was produced, someone has to stand in front of them and explain it — not delegate the explanation to a tool.

It will need to be adapted. Not just for the regulatory changes that are announced, but for the ones that can be anticipated if you're paying attention to the right signals.

Building for longevity means accepting this from the start — and staffing, budgeting, and designing accordingly. The organisations that internalise this build differently. The ones that don't will keep paying for the lesson.

Automation complete is not the end of the story. It is where the real work begins.

---

## Chapter 4 — AI时代的低代码 (Low-Code in the Age of AI)

Accept the premise of Chapter 3 — that the real cost of automation is in what comes after go-live — and a harder question follows: which tools are actually designed for that reality?

This is the question most institutions are not asking clearly enough. The tool debate in financial services tends to focus on capability and speed: what can be built, how fast. The lifecycle question — what can be owned, maintained, audited, and adapted over time, by the people who actually have to live with it — gets much less attention.

AI has made this harder to think about clearly, not easier.

### The black box problem doesn't disappear with AI

When AI generates code that nobody fully designed and nobody fully understands, the maintainability problem isn't solved. It's relocated.

The logic is invisible. The assumptions are undocumented. The edge cases are buried. The next person to touch the system inherits not just code, but a mystery — exactly the situation I found at JPMorgan, except now the mystery was produced by a model rather than a person.

Some will argue that this doesn't matter: if AI can write the code, AI can also read it, explain it, and modify it. This is partially true and dangerously incomplete.

It's partially true because AI can, in many cases, parse and explain code it didn't write. But it misses three things.

First, auditability in regulated environments is not satisfied by AI explanation. When a regulator asks how a number was produced, the answer must come from a person who understands the system — not from a model that interprets it on demand. The audit trail must be human-readable and human-defensible. "I asked the AI to explain it" is not an audit trail.

Second, AI-mediated understanding creates a new dependency chain. Today's model can read today's code. Tomorrow's model may behave differently, interpret edge cases differently, or simply be unavailable when something breaks at 11pm before a submission deadline. You've replaced one black box with another — and the new one is less stable and less accountable.

Third, and most fundamentally: maintaining a system in a regulated environment is not primarily a code-reading problem. It is a judgment problem. Which of these regulatory requirements actually applies here? Is this anomaly a data quality issue or a logic flaw? Should this change be absorbed at the model layer or the reporting layer? These questions require someone who genuinely understands the system — not someone who can query a model about it.

### What low-code solves that AI doesn't

Low-code tools and AI are not alternatives. They address fundamentally different problems.

AI accelerates generation. Low-code enforces visibility. In regulated environments, visibility is not optional — it is a prerequisite for auditability, maintainability, and genuine knowledge transfer.

Every transformation step in a low-code pipeline is explicit. Every logic change is traceable. The visual flow maps directly to the business logic — which means a regulator can be walked through it without an interpreter, a new team member can understand it without decoding someone else's code, and a business user can make controlled adjustments without IT involvement.

This is not a limitation of low-code tools. It is their core value proposition in environments where transparency is a requirement.

AI can, and should, accelerate the work done within low-code environments — helping design logic, identify edge cases, generate configuration. But it cannot substitute for the structural visibility those environments provide.

### The lifecycle question, restated

The institutions cycling between Python, low-code, and AI are not being agile. They are paying the switching cost repeatedly because they have never clearly answered the question Chapter 3 poses: what does it actually cost to own this system over its full operational lifetime?

Over three years, over five years — accounting for every regulatory update, every audit request, every staff transition, every edge case that surfaces after go-live — the calculus consistently favours transparency over raw capability.

The institutions that will navigate the AI transition well are not necessarily the ones moving fastest. They are the ones that have thought clearly about what transparency and auditability require in their specific context — and make tool choices that serve those requirements, rather than ones that trade them away for speed.

*Tools can replace what you do. They cannot replace how you think.*

---

*[Back to Architecture & Design Decisions](ARCHITECTURE.md)*
