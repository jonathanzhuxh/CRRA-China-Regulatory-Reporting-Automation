# Sustainable Digitalisation Why I Designed a System to Make Itself Unnecessary

In most organisations, job security comes from being indispensable.

You know the system. You understand the logic. You’re the only one who can fix it when it breaks. This feels like protection. In the short term, it is.

But there’s a cost that rarely gets calculated: when you’re the single point of failure, the system stops being yours and starts owning you.

## Where this belief came from

It didn’t start as a philosophy. It started as a fear.

At JPMorgan, I inherited a regulatory reporting process with no documentation, no handover notes, and no institutional memory. The person before me was gone. The logic lived nowhere except in the system itself — and the system didn’t explain itself.

I spent months reverse-engineering what should have taken days. Eventually I built a solution. It worked. But then a new problem surfaced: what happens when I go on leave? What happens when I leave entirely?

That question changed how I thought about building things.

Around the same time, COVID had made professional developers scarce. I was pushed into building automation myself — not by choice, but by necessity. I picked up Alteryx, then Dataiku. And somewhere in that process, the fear became a principle:

*Whatever I build, it cannot depend on me to survive.*

## Why I chose low-code — and why it wasn’t just about convenience

The obvious reason for choosing low-code tools was pragmatic: I wasn’t a professional developer, developers weren’t available, and the work needed to get done.

But the deeper reason was sustainability.

Python was an option. I considered it. I rejected it — not primarily because of my own skill level, but because of what Python-based systems look like to the people who inherit them. Even experienced developers struggle to read each other’s code. Expecting business users in a Finance department to maintain a Python pipeline is not a digital transformation strategy. It’s a hostage situation.

At Standard Chartered, there were genuine discussions about training business users in Python. I thought this was optimistic to the point of fantasy.

Low-code tools solve a different problem. Every transformation step is visible. Every logic change is traceable. The visual flow maps directly to how people already think about data in Excel — which means the learning curve is shallow enough that real adoption actually happens. At Standard Chartered, Finance team members with no technical background learned to maintain parts of the system themselves. Not at a sophisticated level — but they weren’t blind to it either. They could open it, follow it, and fix simple things without calling IT.

That’s not a small thing. That’s the difference between a system that outlives its creator and one that doesn’t.

## The choice I made

In 2022, I was tasked with rebuilding a regulatory reporting system from scratch. 900+ reports. 20+ branch entities. Two regulators with different frameworks and conflicting data requirements.

I could have built something only I could maintain. In a bank, that’s not even a conscious decision — it’s the default. Complexity accumulates naturally. Documentation doesn’t. Knowledge concentrates in the person who built the thing, and that person becomes difficult to remove.

I made a different choice.

Every design decision was evaluated against one question: can someone else maintain this without me?

The data model was decoupled so business users could manage regulatory logic changes without IT involvement. The pipelines were built transparently so any technically literate person could trace exactly how any output number was produced. The documentation was written so the system could be handed over cleanly — and it was.

I left. The system kept running.

## What this looks like at three levels

Sustainable digitalisation isn’t a single decision. It’s a principle that has to be applied at every level.

At the system level, it means no black boxes. Every calculation visible, every logic traceable. A system that depends on its creator’s memory is not a system — it’s a liability.

At the human level, it means transferring knowledge deliberately and completely. I trained the team not just to use the system but to own it. The goal was to make my continued involvement unnecessary, not to make myself the guardian of institutional knowledge.

At the organisational level, it means designing for impact beyond your own tenure. The architecture I built was eventually adopted as the standard for all future automation initiatives across the department — extending beyond the original scope, outliving the platform it was built on, and continuing to influence how teams work long after I left.

The system outlived its platform. The methodology outlived the system.

## Why most people do the opposite — and why AI is making that more expensive

The instinct to make yourself indispensable is understandable. In organisations that reward tenure over impact, being the only person who understands something feels like safety.

But it’s a short-term trade. You become harder to remove, and also harder to promote. You become the person who maintains the thing, not the person who builds the next thing.

AI has made this trade significantly more expensive.

The anxiety many people feel about AI is real — but I think it’s misdiagnosed. The fear isn’t really about AI. It’s about having spent years building indispensability through execution rather than judgment. When a tool arrives that can execute faster and cheaper, the foundation of that indispensability collapses.

But here’s what I think most people are missing: AI vibe coding doesn’t eliminate black boxes. It creates new ones.

When AI generates code that nobody wrote and nobody fully understands, you haven’t solved the maintainability problem — you’ve outsourced it to a model that won’t be there when something breaks at 11pm before a regulatory submission deadline. The logic is invisible. The assumptions are buried. The next person inherits not just a system, but a mystery.

Low-code tools are the opposite of this. They are, in a sense, deliberately limited — every step explicit, every transformation visible, every assumption surfaced. That “limitation” is precisely their value in environments where transparency and auditability are not optional.

AI makes execution cheap. It does not make judgment cheap. It does not make transparency automatic. And it does not make a system maintainable by the people who have to live with it.

Tearing down black boxes requires tools that refuse to build them in the first place.

## The counterintuitive truth
The most durable form of job security is building things that don’t need you.

Not because it makes you dispensable — but because it frees you to keep moving. Every system you build that runs without you is proof that your value is in the thinking, not the doing. And thinking, unlike doing, compounds.

I designed a system to make itself unnecessary. Then I left.

My biggest regret is not that I made myself replaceable. It’s that most organisations aren’t structured to reward people who think this way — yet.

That’s changing. Slowly. But it’s changing.

***Tools can replace what you do. They cannot replace how you think.***
