# Collect Once, Consume Many

Here's a pattern I keep seeing, in my own systems and everywhere else.

One data source — an Excel report from a partner, an API from a vendor, a folder where files get dropped. And around it, over time, three or four different systems each grow their own little arm reaching into it. One team write a parser for their tool. Another team write another parser, for the same file, for their tool. A third one pull the same API on their own schedule, map the fields their own way.

Nobody planned this. It just happen, one reasonable decision at a time. Each team needed the data, the fastest path was to grab it themselves, so they did.

Then one day the partner change the Excel format. One column renamed. And it break in four places, on four different schedules, discovered by four different people, fixed four slightly different ways. Or the quieter version, the worse one: it break in only three places, the fourth parser keep running on wrong assumptions, and now two systems disagree about the same fact and nobody know which one to trust.

The fix I settled on is one rule: any fact enter the ecosystem exactly once.

One collector own the boundary to each source. It read the Excel, pull the API, watch the folder — whatever the source need — and convert what it find into one standard shape. An envelope: what happened, where it came from, when. The collector doesn't interpret business meaning, doesn't decide anything. It just turn outside mess into inside fact, once.

Everything downstream consume the envelope. Rule evaluation read it. The observability side read it. Tomorrow's system I haven't built yet read it. None of them know or care whether the source was Excel or API or a scanned PDF — that knowledge live in exactly one place.

Now when the partner rename that column, one collector break, one fix ship, every consumer heal at the same time. And two systems can't disagree about the fact anymore, because they're literally reading the same fact.

The rule cost something upfront — building a collector feel slower than just parsing the file right where you need it. Every team feel that. That's exactly why everyone grab their own copy in the first place.

But data source multiply, and consumers multiply faster. The question is never whether you'll pay for the boundary. It's whether you pay once, at the door — or every time, everywhere, forever.
