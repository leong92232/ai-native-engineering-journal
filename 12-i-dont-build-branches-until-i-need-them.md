# I Don't Build Branches Until I Need Them

When I start building my own workflow engine, first thing everyone expect is branching. Conditions, parallel paths, if-approved-go-here-else-go-there, the whole diagram with diamond shapes.

I didn't build any of it. My workflow is a straight line.

Idea, then Need Pictures, then Pictures Ready, then Prompt Ready, then Generate, then Review, then Done. One direction. No fork.

Not because branching is hard to code. Honestly the code is not the hard part. The hard part come after — every branch double the paths you have to think about. Testing double. Explaining to another person double. "What state can this task be in right now" stop having a simple answer. And most of that complexity, you pay for it upfront, before any real case ever ask for it.

Here's what I notice about how people design workflow: they imagine branches. They sit in a meeting and go, "what if the review fail? what if the owner is on leave? what if we need parallel approval?" — and then they build all of it, day one. For scenario that may never happen, or happen different from imagined.

I go the other way. Straight line first. When a real case hit the wall — an actual task, actually stuck, because the line can't express what need to happen — then I look at it. And even then, my first question is not "how do I add a branch." It's "can this be a separate linear workflow instead?"

A rejected review doesn't need a branch. It can just be a step back — Review goes back to Generate. Still a line. A special approval path for one customer doesn't need a condition inside the flow. It can be its own template, its own straight line. Two simple lines are easier to live with than one clever tree.

Maybe someday a real case will genuinely need a branch, and I'll add it — one, that specific one, paid for by an actual problem. That's the difference. A branch I add for a real case earn its complexity. A branch I add in a design meeting is just my imagination, running in production.

Straight line until proven otherwise.
