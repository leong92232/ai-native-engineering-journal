# Approval Is Not a Boolean Flag

Last year, during a takeover session, I found approval implemented as a bit.

One column, one flag. Approved or not approved.

It's a very common way to do approval, and I don't think it's wrong. A boolean is the fastest thing to write, the easiest thing to trace, the easiest thing to troubleshoot at 2am when something breaks. When engineers are debugging, they want a flat line — one column, one value, one place to look.

But sitting with that code, I started asking a simple question: is approval really just a boolean?

Can approval have next steps? Can it lead somewhere?

It turns out it usually does. There's often more happening after "approved" — a follow-up action, a downstream state, sometimes a consolidation step where multiple approvals come together into one outcome. Most of the time, that logic still gets written. It just gets written manually, in application code, sitting on top of the flag. The developer checks `if approved == true`, then branches into whatever comes next by hand.

That's not wrong either. It works. But it means the flag is doing less than the process actually needs, and the real logic — the sequence, the state, the "what happens next" — lives scattered across the codebase instead of being named anywhere.

There isn't one definitive right answer here. Boolean will always be the fastest path in a pure engineering sense. But I think the standard is shifting.

We're in an AI era now. Systems need to describe intent, not just record a checkbox. A flat line — one flag, one branch — is fast to write but slow to reason about once the "what happens next" starts growing. We need something closer to linear: approval as a sequence, a state, a step that leads to the next step, not a switch that engineers privately wire up in code.

The way I've been resolving this: the decision itself can be stateless, but the approval must still be recorded.

The evaluation — should this be approved, given the current facts and rules — doesn't need to hold any state of its own. It just answers a question. But the moment approval happens, that's a real business event. It has to be recorded, audited, and owned by the application, not left as a side effect of a flag flipping somewhere.

```
Candidate (fact, from discovery)
-> Evaluate(candidate, rules)   [stateless decision — should this be approved?]
-> ApproveCandidate()           [named action, owned by the app]
-> WatchlistItem                [recorded state, with audit trail]
```

So the split is:

- **The decision engine is stateless.** It answers "is this approvable, and what should happen next" — nothing more.
- **The application owns the event.** It records that approval happened, when, and what it triggered.
- **Approval itself is never a lonely boolean.** It's a named action with a moment, a reason, and a downstream effect.

The principle I keep coming back to:

> A flag can tell you the current state. It can't tell you what decided it, or what happens next. That has to live somewhere — either in an action the system remembers, or in code nobody remembers writing.

Boolean will always be faster to write. But in an AI-native system, the thing worth optimizing for isn't how fast you can write the check — it's whether the system can still explain itself six months later.
