# Actions Don't Change State. Effects Do.

I used to write it simple. User click Approve, code go straight in, change the status column, done. One button, one write.

Work fine, until I want to know later, why did this change happen, and what else happen because of it.

If Approve just call an UPDATE statement, the only thing recorded is the after-state. Not what actually happened. Not what else fire off along with it — maybe also assign new owner, maybe also send notification, maybe also unlock next task. All of that get buried inside the same function, no name, no trace.

So I stop writing Action as one lump of code doing everything.

Now Action produce Effects. Action itself is just a name, a moment — Approve happen. It doesn't touch the database directly. It produces a list: ChangeState, AssignOwner, SendNotification, maybe CreateNextTask. Then something else, an Effect Runner, actually go execute each one, one at a time, and write down that it happened.

I saw this play out literally, small scale, in my own workflow tool. One action, "Request Pictures" — it didn't do one thing. It did two: change state from Idea to Need Pictures, and assign owner to Bruce. Both effect, same action, both recorded separately in the history. If I only logged "Approved" as one line, I'd lose which part was the state change and which part was the ownership change. Now I can see both, and later, replay either one, or simulate what would happen without actually running it.

That's the part I didn't expect going in — once Action is separated from Effect, I get things for free. Audit trail, because every effect is its own recorded line, not folded into a black box. Simulation, because I can run the effects through a dry pass and see what would change, before it actually change. And AI review, because I can hand a reviewer — human or AI — a clean list of effects and ask "does this look right," instead of asking them to reverse-engineer what a function actually did from reading code.

Action answer "what happened."

Effect answer "what changed, and how do I prove it."

I stop trusting a button to change my system directly. I let it name what should happen, and let something else be responsible for actually doing it.
