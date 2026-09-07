markdown
# Why EDI Still Wins, Even Though Everyone Hates It

Every engineer who touches freight for the first time asks some version of the same question: why is this industry still running on fixed-width flat files and decades-old message standards, when modern APIs and event streaming have existed for years?

It's a fair question on the surface. The formats really are old. The tooling really is clunky by modern standards. Nobody chooses EDI on its technical merits if they're starting from a blank page today.

But that's exactly the tell. Almost nobody in this industry is starting from a blank page.

The real cost of EDI was never the format itself. It's the number of independently negotiated relationships sitting on top of it. A single freight company doesn't have one EDI connection — it has one per trading partner, and each of those was set up separately, often years apart, often by different people, often with small partner-specific deviations baked in. Replacing the format doesn't mean upgrading one system. It means touching every one of those relationships, more or less simultaneously, because a shared format only works if both sides agree to move together.

That's a switching-cost problem, not a technology problem. And switching cost that's dominated by the number of counterparties, not by the complexity of any one connection, behaves differently than ordinary technical debt. Normal technical debt gets worse gradually and can be paid down incrementally, one module at a time. This kind can't — a partial migration just means running two formats at once, which is usually more expensive than running the old one alone.

I'll state my actual claim carefully, because it's a judgment, not a measured fact: absent something forcing the industry's hand — a major partner who simply won't accept the old format anymore, a regulatory mandate, or a cost shock that changes the math — the rational move for an established player is to keep paying EDI's ongoing tax rather than pay the far larger one-time cost of moving the whole partner network at once. That's not a claim I can point to a study for. It's a read on incentives, and I could be wrong about how close any given company is to its own forcing function.

The counterexample is worth naming directly, because it's the case that actually proves the mechanism rather than contradicting it: greenfield operations, and some freight-tech entrants building partner networks from scratch, do run on modern APIs from day one. That's not evidence that EDI is technically superior, or that established players are simply behind. It's evidence for the opposite — the constraint was never the format, it was the existing partner count. Zero legacy partners means zero switching cost, and the same company that resists a migration on day 3,000 would happily start clean on day one.

What I haven't seen enough of yet, and want to flag honestly rather than guess at: whether a new generation of freight-tech networks, built API-native from the start, eventually reaches enough partner density that it starts pulling established players over — not by winning an argument about formats, but by becoming a partner too large to keep running EDI-only. I think that's plausible. I don't have evidence yet that it's happening at meaningful scale.

> EDI doesn't persist because the industry hasn't noticed better options. It persists because the cost of switching was never about the format — it was always about how many relationships have to move at the same time.

Technology conservatism would predict this industry avoids new formats out of habit. What actually happens is closer to a correctly priced hesitation — an accurate read of what re-platforming a partner network actually costs, versus what it's rumored to cost from outside.
