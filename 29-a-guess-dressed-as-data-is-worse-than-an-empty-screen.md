# A Guess Dressed as Data Is Worse Than an Empty Screen

We had a "today's tasks" panel that looked helpful. It showed up every morning, populated, confident, ready.

The problem: half of what it showed wasn't real. It was a heuristic guessing at what probably needed attention, based on patterns that used to hold and mostly still did — until they didn't. Nobody could tell, just by looking at the panel, which numbers were actual pending work and which were the system's best guess dressed up to look like a fact.

That's a dangerous kind of wrong. A broken feature is obvious — it's empty, or it errors, or it says "no data." People route around it. A confidently wrong feature is worse, because it looks exactly like the working version. Nobody double-checks a number that looks normal. They just act on it.

We finally killed the heuristic. Not improved it, not tuned it — turned it off, and left the screen empty until there was a real source of truth behind it.

That felt uncomfortable for about a day. An empty panel looks like a regression. People notice absence immediately, the way they never noticed the guess.

But that discomfort was the point. An empty screen tells the truth: we don't know yet. A guess dressed as data tells a lie that's shaped exactly like the truth, and the only way to catch it is to already know better than the system does — which defeats the purpose of having the system at all.

The principle I landed on:

> If you can't stand behind a number, don't show a number. Show nothing, and let that absence pressure someone to build the real thing.

This isn't a case against inference, or against AI making a best guess when asked. It's a case against a guess quietly wearing the same clothes as verified data, sitting in the same UI slot, with no visible difference between "we checked" and "we assumed."

The fix wasn't smarter guessing. It was making the system honest about the difference between what it knows and what it's estimating — and when it can't tell the difference itself, defaulting to silence over confidence.

An empty screen is honest. A wrong number that looks right is a debt collected later, usually by someone who trusted it.
