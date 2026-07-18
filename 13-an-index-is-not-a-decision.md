# An Index Is Not a Decision

I built a file index service. Simple job: files come in, it stores them, tags them, remembers what arrived and when. Any system can ask it — is this document here yet, which files do we have for this job.

Then the first real use case show up, and with it, the first temptation.

The business need is: when all three required documents arrive, start the next process. And the index service is the only one who know the moment the third file land. It has the information. It's right there. So the obvious design is — let the index fire the trigger. File complete, index call the next system, process start.

I almost did it. It's one webhook. Maybe ten lines.

But look at what those ten lines actually are. "All three documents" — that's a business rule. Which three? Depend on the job type. Can two be enough if one has an exception approved? That's another rule. Should it still trigger after office hours, or wait? Rule again. The moment my index fire that trigger, every one of those rules need to live inside the index service. And next month when the business change "three documents" to "four", somebody has to remember the file index is where that logic went to live.

An index that start making decisions stop being an index. It quietly become another app — one nobody design to be an app, so it become a badly designed one.

So I hold the line. The index answer questions about files: what arrived, when, what's still missing. That's all. It can announce a fact — "a file arrived" — but announcing a fact is not the same as deciding what the fact mean.

The decision live with the caller. The system that own the business rule ask the index: are the documents I need here? Index say yes or no. Caller decide what to do about it. If rules change, they change in the caller, where all the other rules already live — not scattered into a storage service because it happened to be standing closest to the event.

The test I use now, whenever a service "could easily" trigger the next step: does this service own the rule for when to trigger? If not, it doesn't get to pull the trigger. Knowing something happened doesn't earn you the right to decide what happen next.

An index tells you where things are.

It should never tell the business what to do.
