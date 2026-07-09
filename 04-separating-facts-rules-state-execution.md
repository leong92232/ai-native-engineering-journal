# Separating Facts, Rules, State, and Execution

Over the last few articles I kept circling back to the same complaint, phrased differently each time.

First it was: a rule engine slowly turns into an application if you let workflow status, ownership, and notifications leak into it.

Then it was: approval is not a boolean flag, because a flag can't hold the moment a decision happened or what it triggered next.

Then it was: workflow is better than settings, because settings describe values while real processes describe behavior.

Three different complaints. Same root cause.

Every one of those systems was mixing up four things that don't belong in the same place:

Facts. Rules. State. Execution.

I only noticed the pattern once I tried to name each one on its own.

**Facts** are what happened. A form was submitted. A price came in. A file arrived. Facts don't say what they mean. They just say that they occurred, and when.

**Rules** take facts and current state, and answer one question: given this, what should happen next. A rule doesn't remember anything between calls. It's not supposed to. Ask it the same question twice, get the same answer twice.

**State** is what the system currently believes is true. Which stage a task is in. Who owns it. Whether it's overdue. State is not a fact — it's a conclusion the application is willing to stand behind, and it changes only through...

**Execution**. The actual act of moving state forward. Approving something. Assigning someone. Sending a notification. Execution is where consequences happen, and it's the one layer that must be audited, because it's the one layer that changes the world.

Once I had these four named separately, I could go back and see exactly where each of my earlier design smells came from.

The rule engine problem was rules quietly absorbing state and execution. It started answering "what should happen" and ended up also remembering "did it happen yet."

The approval problem was state and execution collapsing into a single fact. A boolean flag looks like a fact, but it was actually standing in for a state transition that nobody named.

The workflow problem was rules disguised as settings. `reminder_days = 3` looks like a fact you configure. But "notify the supervisor when a task is overdue and unanswered" is a rule producing execution — it just never got named as one.

Different failure, same missing separation.

The version of this I keep coming back to now:

> Facts are collected. Rules are evaluated. State is owned. Execution is audited.

None of these needs to be complicated. A fact can be one row in a table. A rule can be one function. State can be one column, as long as it's a real column and not five overloaded booleans standing in for it. Execution can be one method, as long as it's the only method allowed to touch that column.

What matters isn't the sophistication of any one layer. What matters is that each one stays in its lane, so that six months later, when someone asks "why did this happen," the answer is somewhere you can point to — not somewhere you have to reconstruct from scattered conditionals.

That's the test I use now when I look at a new piece of code: which of these four things is this, and does it know it?
