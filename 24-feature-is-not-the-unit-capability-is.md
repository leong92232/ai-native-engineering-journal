# Feature Is Not the Unit. Capability Is.

Saved this one for last, because everything else I've written come down to it.

Every conversation about software happen in features. Users ask in features — "can it remind me when the task is overdue." Roadmaps are lists of features. Teams measure themselves in features shipped. Nothing wrong with that. Feature is the natural unit of conversation.

The trouble start when feature also become the unit of construction.

Build feature by feature, and each one become its own little tunnel through the codebase. The overdue reminder get its own trigger check, its own condition logic, its own email code. Next month, "notify supervisor on escalation" — new tunnel, own trigger, own condition, own notification code, slightly different. Thirty features later you have thirty tunnels, some crossing, none aware of each other. Every new feature make the system heavier. None make it stronger.

The alternative unit is capability: a thing the system can do, named, with a boundary, built once. Evaluate rules against a state. Send a notification. Parse a document into facts. Track a state machine. Record an audit trail. Grade an outcome.

Then features stop being construction. They become composition. "Remind me when overdue" is not a project anymore — it's a rule (existing capability) plus a notification (existing capability) plus a schedule (existing capability). Wiring, not tunneling. And here's the compounding part: when a feature request genuinely can't compose from what exist, that's the signal you found a missing capability — build that, properly, with a boundary, and every future feature get cheaper. Feature-built systems get heavier with each request. Capability-built systems get stronger.

Looking back, this whole journal has secretly been one argument. Why the rule engine must stay a rule engine — because it's a capability, and capabilities keep their boundary. Why the index doesn't decide, why the observer doesn't fix, why facts get collected once — same sentence, different rooms.

And it matter more right now than ever, because AI removed the cost of producing features. Ask, and working code arrive. Which mean the feature factory now run at machine speed — and if feature is your unit, so does the tunneling. A hundred AI-built features can leave you a platform or a pile, and the code itself won't tell you which. The unit you were building in decide that, long before any single feature was written.

Features are what people ask for. Fine.

Capabilities are what a system is. Build those.
