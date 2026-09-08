# You Don't Need Blockchain. You Need What Blockchain Promised.

A few years ago I spent real time on a blockchain project in this industry — not reading about one, building toward one. That's where this entry comes from, not from watching the hype cycle from outside.

The pitch was always the same: a shipment record that no single party can quietly alter after the fact. Multiple parties — carrier, forwarder, customs, sometimes the customer — all needing to trust the same history of events, without any one of them controlling the record everyone else has to accept. Decentralization was the mechanism on offer. Nobody trusts a ledger owned by one party, so let no party own it.

That's a real problem, and it's worth taking seriously on its own terms before reaching for a solution.

Where I think the industry got ahead of itself is in treating decentralization as the goal, rather than as one possible means to a narrower goal: tamper-evidence. What people actually wanted was the ability to say, with confidence, "this record hasn't been quietly changed since it was written" — not "this record is held by no one in particular." Those are different properties, and blockchain bundles them together whether or not you need both.

If tamper-evidence is the actual requirement, there's a much cheaper way to get it: a hash-chained, append-only audit log. Each entry cryptographically references the one before it, so altering any past entry breaks every hash after it — the same tamper-evidence property blockchain offers, without needing consensus across nodes, without transaction fees, without the operational weight of running or coordinating a distributed ledger. One party can host it. Anyone can verify it independently, because the verification is math, not trust in the host.

I want to be honest about where this substitution actually breaks down, because it does. A hash-chained log held by one company still requires everyone downstream to trust that company enough to accept its hosting — the mathematics prove nothing was altered after the fact, but they don't prove the log wasn't selectively omitted before anyone else looked. Genuine multi-party settings, where no single participant is trusted enough to host the shared record at all — a consortium of competitors, for instance, none of whom will accept a rival hosting the ledger — is the case where decentralization itself is the requirement, not just an expensive way to get tamper-evidence. That's the case blockchain was actually built for, and in that specific case, I don't think the cheaper substitute holds up.

Most freight scenarios I've encountered aren't that case. They're a bilateral or hub-and-spoke relationship — one party is already trusted enough to host the source system everyone else already queries. In that setting, paying for consensus infrastructure buys a property nobody was actually missing.

This connects to something I've written about before, from a different angle: an application's audit trail deserves to be a first-class part of its architecture, not an afterthought bolted on later. A hash-chained log is that principle taken one step further — not just "record what happened," but "record it in a way that makes tampering provably visible," which is the specific promise blockchain made, minus everything it charged for that this problem never needed.

> The valuable part was never the chain of computers verifying each other. It was the property that a record, once written, stays honest. You can buy that property far more cheaply than the infrastructure that made people notice they wanted it.

Ask what you actually need before asking which technology promises to deliver it. In this case, most of the industry needed a smaller, older idea — the append-only log — dressed up in a much bigger, much newer one.
