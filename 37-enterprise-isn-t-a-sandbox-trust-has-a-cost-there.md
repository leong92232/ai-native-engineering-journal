# Enterprise Isn't a Sandbox — Trust Has a Cost There

It's easy to let AI handle a deployment step. Update a config, adjust a migration, touch an environment variable. It's fast, it's usually right, and after enough times of it being right, the habit of checking recedes.

Then something breaks in production, and the first question isn't "what broke" — it's "what changed." And that's where the cost that felt free shows up all at once.

In a sandbox, this doesn't matter much. The blast radius is small, the stakes are low, and if AI got something wrong, you notice quickly and fix it without anyone downstream feeling it. Enterprise systems don't work that way. A deployment change touches other services, other teams, other people's assumptions about what's stable. When something breaks there, the debugging isn't "check the last commit." It's "reconstruct what actually changed, across however many steps got delegated, before you can even start diagnosing why."

That reconstruction step is the bill. It was never free — it just didn't come due until the incident, and by then it's larger than it would have been if a human had made the change slowly, understanding it the whole way through, instead of fast and unexplained.

This isn't an argument for reviewing every AI action at sandbox-level caution everywhere. That defeats the point of using AI at all. It's an argument for knowing which actions sit in the category where a mistake is cheap to notice and reverse, and which sit in the category where a mistake is expensive to even *locate*. Deployment, production configuration, anything touching shared infrastructure — that's the second category, by definition, because the whole point of shared infrastructure is that a change to it doesn't stay contained.

> The efficiency you gain by trusting AI with a deployment step gets paid back with interest the first time something breaks and nobody can explain what changed or why.

The fix isn't "trust AI less everywhere." It's "know where the enterprise line is, and don't let a habit formed in low-stakes territory quietly walk itself into high-stakes territory because it worked fine the last twenty times." Enterprise isn't a bigger sandbox. It's the place where the cost of an unexplained change stops being small.
