# How I Tell If AI Coding Is Actually Working, Not Just Looking Fast

Fast is easy to see. Demo look good, feature arrive early, everyone happy.

But fast is also the easiest thing to fake — not fake on purpose, just... fast output look the same whether the thinking behind it is solid or not. A confident-looking pull request tell you nothing about whether anyone actually decided anything.

So I stop judging by speed. I look for three trace instead. None of them need me to read a single line of code.

**One — can someone show me what was decided before the code was written?**

Not after. Before. A short design note, a process flow, even a rough document saying what we're building and what happen when things fail. If the only artifact that exist is the code itself, that mean nobody decided — the AI decided, and the team just accepted. When I ask "why is it done this way" and the answer is "that's how it came out," that's the tell.

**Two — did anyone other than the author actually push back?**

Not approve. Push back. Somewhere in review there should be at least one "why this, not that," one question the author had to actually answer. If every review is a quiet thumbs-up, review isn't happening — it just look like it is. And this include AI reviewing AI: if the same session that wrote the code also checked the code, that's not a check. That's the author agreeing with himself.

**Three — when something break, how long until we know why?**

This is the one that show up late, so most people miss it. Fast code with no decision trail is cheap to write and expensive to debug. If a problem take days to trace because nobody can say what the code was supposed to do, all the speed from earlier just got paid back — with interest. But if the team can point to the intent, point to what changed, point to who checked it — the fix is fast too. Speed that survive the first incident is real. Speed that die at the first incident was borrowed.

Notice what's not on this list: how many lines, how many features, how fast the demo came.

Output tell you the AI is working.

The trace tell you the team is.
