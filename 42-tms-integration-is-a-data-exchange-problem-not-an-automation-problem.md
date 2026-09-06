markdown
# TMS Integration Is a Data Exchange Problem, Not an Automation Problem

Most TMS integration projects get sold internally as automation projects. Stop re-keying a status by hand. Auto-generate the customer update. Cut the manual step out of the process.

That framing isn't wrong, but it puts the emphasis in the wrong place, and I've seen the consequence of that more than once: a project scoped as "automate this handoff" runs into months of unplanned work, and the automation itself was never the hard part.

The hard part is that the two systems on either end of the handoff don't agree on what the data means.

A transport milestone from one carrier isn't the same shape as a milestone from another. A status code that means "departed" in one feed can mean "manifested, pending departure" in another. Two systems can both claim to send "the same event" and disagree, in practice, on what actually happened and when. None of this shows up as a bug. Each side is doing exactly what its own system was built to do. The mismatch lives in the gap between them, in the part neither system's documentation fully owns.

This is why the automation framing misleads people. Automating a manual step assumes the data underneath is already trustworthy and already means one consistent thing. Integration work is usually the point where you discover it doesn't — carrier by carrier, sometimes leg by leg.

I want to be precise about what I'm claiming here, because it's easy to overstate. This isn't true of every integration. A pilot connecting two well-documented, standards-compliant systems can genuinely be closer to an automation problem — the mapping is clean, the field definitions match, and the project really is "stop typing this by hand." The pattern I'm describing shows up specifically at scale, across many counterparties, where each one has quietly deviated from the standard it claims to follow. A demo with one clean data source won't surface this. A rollout across a real carrier network usually will.

Where I've seen this play out directly: pulling transport-system events into a stakeholder-facing visibility layer isn't really an automation task. It's an exercise in separating two things that get conflated — what a source system actually reported as a fact, and what that fact should be interpreted to mean for the person looking at a dashboard. Skip that separation, and the visibility layer inherits every quirk of every source system, silently, and nobody downstream can tell which numbers to trust.

This is where I think AI genuinely earns a place in this kind of work — not as the thing that decides what's true, but as the flexible translation layer between formats and dialects that would otherwise need a hand-written mapping for every carrier variant. Rigid field-to-field mapping code breaks the moment a GHA or carrier deviates from spec, which happens constantly in practice. A model that can be shown the source structure and asked to reconcile it against a target schema adapts to that variation far more cheaply than another engineer writing another one-off parser.

I'd flag one honest limit here rather than skip past it: I haven't seen enough volume of this specific pattern — AI-assisted mapping against messy, non-standard carrier data — to say how it holds up on the fields that carry real financial or regulatory consequence, like customs declarations or invoicing figures. My instinct is that this is exactly the boundary where a human still has to check the mapping before it's trusted, not after. But that's a judgment based on the shape of the risk, not on a track record I can point to yet.

The principle I keep coming back to:

> An integration project doesn't fail because nobody automated the handoff. It fails because nobody agreed, in enough detail, on what the data crossing that handoff actually means.

Automation is the easy 80%. Reconciling meaning across systems that were never built to agre
