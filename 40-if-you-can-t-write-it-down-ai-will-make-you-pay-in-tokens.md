markdown
# If You Can't Write It Down, AI Will Make You Pay in Tokens

I noticed something in a team I was working with recently: requirements moved fast in conversation, and almost never made it into a written user story.

That's not a knock on the team. Verbal communication like that works — when it works — because the two people already share years of context. A half-sentence lands, because both sides fill in the rest from memory: what this system does, what "urgent" usually means here, what got skipped last time and why. None of that context is written down anywhere. It doesn't need to be. It lives in the relationship.

Then AI enters the loop, and the same half-sentence gets handed to it.

AI has none of that shared history. It can't read tone, and it can't recall the hallway conversation from three weeks ago that would have disambiguated the ask. So it does one of two things: it stops and asks clarifying questions, burning a round trip, or it guesses — and builds the wrong thing confidently, which costs far more to unwind than the clarifying question would have.

Either way, someone pays for the ambiguity. The bill just moves to a different currency: tokens, retries, and the hours spent noticing the guess was wrong.

I want to be careful with the claim here, because it's tempting to overstate it. This isn't "people who talk instead of writing are worse engineers." Plenty of strong engineers I've worked with are excellent verbal communicators and thin writers, and it never used to cost them anything, because their listeners were human and forgiving of gaps. The skill that's suddenly expensive isn't communication in general — it's specifically the ability to turn tacit, shared-context knowledge into an explicit, self-contained statement that holds up with no listener history behind it. That's a narrower skill, and it was already unevenly distributed before AI showed up.

It's also worth naming a counterexample: writing a precise user story doesn't guarantee a cheap AI interaction. A beautifully specified story can still eat tokens if the underlying task is genuinely ambiguous, or if the model lacks context that no amount of writing would supply — a legacy system's undocumented behavior, for instance. Precision helps most when the missing piece really is "this was never written down," not when the missing piece is "this was never known by anyone."

What I keep coming back to is that this isn't a new discipline. It's the same one this whole series has been arguing for, just pointed at communication instead of code: separate what's actually known from what's assumed, and don't let the gap hide inside something that looks complete. A rule engine that quietly holds workflow state is the same failure, wearing different clothes, as a user story that quietly assumes the reader already knows what "handle it the usual way" means.

> Verbal fluency works between people who already share the context. AI has none of that context, so a vague ask doesn't get filled in — it gets guessed at, or clarified over several expensive rounds.

Writing precisely for AI was never a new skill. It's the old one — turning tacit into explicit — arriving at a place that used to tolerate skipping it.
