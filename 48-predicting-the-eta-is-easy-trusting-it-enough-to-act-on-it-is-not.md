markdown
# Predicting the ETA Is Easy. Trusting It Enough to Act On It Is Not.

Most of the effort I see going into ETA prediction is aimed at the model. Better features, more historical data, tighter error margins, a few more percentage points of accuracy squeezed out of the training run.

That work is real, and it's not wasted. But in a lot of the cases I've come across, decent ETA prediction has existed for a while, sitting in a system somewhere, mostly unused by the processes that could actually benefit from it. Warehouse labor still gets scheduled off the static transit time in the contract. Customs pre-clearance still waits for a confirmed arrival before starting. Berth or slot booking still runs off the same fixed windows it always has.

The prediction wasn't the missing piece. Somewhere between the model producing a number and a downstream process acting on it, the number stops being used.

I think the actual blocker is accountability, not accuracy. A confirmed fact — a shipment has arrived — has no one attached to the risk of being wrong, because it isn't a prediction, it's an observation. A forecast is different. The moment someone schedules four extra warehouse staff based on a predicted arrival time, and the shipment is late, there's a person who made that call and now has to explain it. Acting on a forecast means accepting a probability distribution instead of a fact, and most operational processes were built around facts, with an accountability structure that assumes something confirmed is what triggered the decision. Nobody redesigned that structure just because a better model showed up.

I want to flag this as my read on the situation, not something I have measured directly. What I have observed is teams with genuinely good ETA models whose output isn't driving the scheduling decisions it could be driving. What I'm inferring — and this is the part I'm less certain of — is that the reason is organizational trust and accountability design, rather than the model still not being accurate enough. It's possible some of these cases really are still accuracy-limited, and I don't have a clean way to separate the two from the outside.

The counterexample is useful here because it shows the pattern can work: dynamic slot booking at some ports already treats an early forecast as provisional, and keeps revising the commitment as the number firms up closer to arrival. That only works because the process was designed from the start to tolerate revision — nobody is penalized for the early number moving, because the system expects it to move, and the final commitment happens close enough to arrival that the residual uncertainty is small. That's a genuinely different design than bolting a forecast onto a process that expects one number and treats it as final.

So the actual work, if the goal is downstream value rather than a better leaderboard score for the model, is redesigning the decision process to expect a forecast that revises over time — building in the fallback for when it's wrong, and deciding in advance who owns that risk instead of discovering it after the fact. That's an organizational and process design problem. It's a different kind of hard than the modeling problem, and I don't think it gets easier by improving the model further.

I don't have a clean playbook for how to shift the accountability side of this — that's more a question of incentive design and organizational trust than something I can reduce to an architecture pattern. I'd rather say that plainly than pretend the technical framing solves it.

> The model was never the hard problem. The hard problem is convincing a process built around confirmed facts to act on something that might still be wrong.

A more accurate forecast that nobody acts on delivers exactly the same operational value as no forecast at all.
