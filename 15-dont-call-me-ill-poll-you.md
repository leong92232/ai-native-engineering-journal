# Don't Call Me, I'll Poll You

Polling has a bad name. Wasteful, they say. Checking again and again when nothing changed. Callbacks are the elegant way — register once, get notified the moment something happen, no wasted call.

I went the other way. In my automation systems, the rule is: no callback. Downstream pull. Everyone poll.

Not because I don't know how webhooks work. Because I watched what callbacks actually cost, and the cost is not in the network — it's in ownership.

The moment system A promise to call system B back, A inherit a pile of problems that used to be B's. A must know who B is, where B live. A must handle B being down — retry, queue, backoff, track which callback got delivered and which didn't. A now hold in-flight state: "I owe B a call." If B move, A change. If B is slow, A carry it. One little callback, and quietly, A's reliability now depend on B's availability.

Multiply that by every downstream. Now the central system carry a list of everyone to notify, retry logic for each, and a growing pile of "did they get it" state. The system that suppose to just answer questions become a dispatcher, then a delivery service, then the thing everyone blame when their notification didn't come.

Flip it around. Downstream poll. Each system ask, on its own clock: anything for me?

The upstream keep nothing in-flight. It doesn't know who its consumers are — doesn't need to. New consumer show up? Zero change upstream, they just start asking. A consumer down for an hour? Nobody else care. When it come back, it ask again, catch up on its own. Failure recovery isn't a mechanism I have to build — it's just the next poll. The whole class of "did the message arrive" problems doesn't get solved, it get deleted.

Yes, I pay for this. Polling has lag — a few seconds, maybe a minute between checks. Most asked calls come back empty. I know. I accept it, because for my workflows, "within a minute" is instant enough, and an empty poll is a lot cheaper than a retry queue with delivery tracking.

The one exception I allow: fire-and-forget. Upstream can shout into a queue, send an email, drop an event — as long as it walk away without waiting for a reply. Announce, don't converse. The line I'm holding isn't "never push." It's "never wait."

Because the real question was never polling versus webhook.

It's: who carry the responsibility when the other side is not there? Callbacks put it on the one who answer. Polling put it on the one who ask.

I want it on the one who ask. They're the one who care about the answer.
