# A Practice Engine, Not a Question Bank

I'm building a learning app for my kid, who's preparing for a big exam. Naturally I looked at what's out there first. And almost everything I found is the same product wearing different skins: a question bank.

Ten thousand questions. Sorted by topic. Sometimes with video explanations. The pitch is always about volume — more questions, more coverage, more content.

But watching my own kid study, I notice content was never the bottleneck. We have plenty of questions — school papers, assessment books, past years. What we didn't have is the loop.

He does a paper. Some answers wrong. We go through them. And then... nothing. The wrong answers just evaporate. Two weeks later, same type of mistake, same trap, like the first time never happened. Not because he's careless — because nothing in the system remembered. The mistake got marked, maybe sighed over, and then it was gone.

That's the difference I ended up designing around:

A question bank stores questions. A practice engine owns the loop.

The loop is: attempt, grade, and then — this is the part everyone skip — track the error as a thing that stay open. Not a statistic, not a red X in a report. An open item, with a lifecycle. It stay open until the system bring that concept back, days later, in a fresh question, and he get it right without help. Only then it close. Wrong again? It stay open, come back sooner.

Because here's the reframe that changed the design: a mistake is not an event to log. It's a task to close. Most apps treat wrong answers as data for a chart — "accuracy 74%." A practice engine treat each one like a bug report: open, being worked, verified fixed, closed. Nobody would run a software team on "bug rate 26%" with no tracking of which bugs. But that's exactly how most studying works.

Same thinking apply to what get served next. A question bank serve what you pick, or random. An engine should serve what's at the edge — not so easy it prove nothing, not so hard it just produce noise. I use the same idea for his chess practice: puzzles selected by current ability, difficulty moving with him. The content sit still; the selection is alive.

I've written a lot about workflow in business systems — state, action, loop, audit. Building this made me realize learning is the same shape. The questions are just content. The learning is in the state machine: what's open, what come back when, what's proven closed.

Content is a library.

Practice is a loop. And the loop is the product.
