# Build vs. Buy Isn't the Real Question. Who Owns the Judgment Is.

The build-versus-buy conversation usually runs on cost and time-to-market. Buying gets you proven functionality faster. Building gets you exactly what you need, eventually, at a price. AI has shifted that calculus — building is genuinely cheaper and faster than it used to be, so more teams are leaning toward build than they would have a few years ago.

I think that's the wrong axis to be optimizing, and it was probably always the wrong axis, AI just made it more visible.

Every system of any complexity embeds judgment. Thresholds for when something gets flagged. Defaults for what happens when data is missing. Rules for which exception gets escalated and which gets silently handled. Whether you buy the system or build it, that judgment exists somewhere inside it. The real question isn't who wrote the code. It's whether your team can explain why the system decides what it decides.

Buy a vendor system, and you're explicitly outsourcing that judgment. That's not automatically bad — a mature vendor has usually made those calls more carefully than a team building the thing for the first time would. But it means when a regulator, a customer, or your own leadership asks "why did the system do that," the honest answer might be "because that's what the vendor decided," and you may not have the visibility to go deeper than that. You bought the judgment along with the software, sight unseen.

Here's where I think AI changes the picture in a way that isn't obviously an improvement: building your own system no longer guarantees you understand the judgment inside it either. If a team leans on AI to generate the rules, the thresholds, the exception handling — and doesn't independently review why each of those decisions was made — they've built a system whose judgment is just as opaque to them as a vendor's would have been. The code sits in their own repository, so it feels like ownership. But if nobody on the team could explain why a particular threshold is 85% and not 80%, that's a black box with better access to the source, not more understanding of the reasoning.

So the real dividing line isn't build versus buy. It's whether someone, on your team, can currently explain the judgment embedded in the system you're running — regardless of who wrote the code that embodies it.

The honest counterexample: plenty of domains are genuinely fine to buy without reinventing the judgment yourself. A standard payment processing ruleset, for instance, encodes judgment that's well-documented, widely reviewed, and would look almost identical if you built it from scratch. There's no real ownership gap to close there, because the reasoning is already legible and stable. The risk concentrates specifically in judgment that's business-specific, still evolving, or consequential enough that "we don't fully know why it does that" is an unacceptable answer.

What I'm less sure of: whether AI-assisted building actually makes teams less likely to interrogate judgment, or whether it just makes it easier for teams who were never going to interrogate it anyway to produce more code faster. I don't have a clean way to separate "AI created this blind spot" from "AI made an existing blind spot more visible, faster." Either way, the fix looks the same: someone has to sit with the generated thresholds and rules and ask why, before they ship, not after something breaks and everyone realizes nobody actually knows.

Build versus buy was never really a sourcing decision. It's a question of who's accountable for explaining the system's judgment when someone asks — and AI didn't change who that has to be. It just made it easier to skip asking.
