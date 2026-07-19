# The System That Only Watches

Most teams have monitoring. CPU, memory, uptime, is the server alive. If something die, alert fire, someone get paged.

But I hit a different kind of problem, and the server monitoring stay completely green through all of it.

The server was alive. The data was wrong.

A source system stop sending one type of record — no error, just silence. Files that suppose to arrive daily came late, sometimes not at all. Two systems held numbers that suppose to match, and quietly didn't. Nothing crashed. Every health check passed. The kind of problem you only discover weeks later, when a human happen to look, and by then nobody can say when it start.

Server monitoring is a heartbeat. It tell you the patient is alive. It doesn't tell you the patient is healthy. I needed something else — less like a heartbeat, more like a health checkup. Not "is the system running," but three different questions about the data itself:

Did everything that should arrive, actually arrive? Did it arrive on time? And where two systems hold the same fact — do they still agree?

So I built an observer for that. And the one rule I set from day one: it only watches. Read-only. It query the other systems, compare what it see against what should be, and when something look wrong, it speak up — push the alert out, instead of waiting for someone to remember to check a dashboard.

That's all it does. And keeping it at "that's all" is the actual design work.

Because the temptation come fast. The observer see a missing file — it know the file is missing, it know who to ask — why not let it re-request the file? It see two numbers disagree — why not let it patch the smaller one? Every anomaly it catch come with an obvious little fix attached, and every fix is just a few lines.

But an observer that fix things is no longer an observer. Now it mutate state, which mean now it can be wrong in a way that change data. Which mean now the other systems have a hidden second writer they don't know about. And the worst part — when data look strange next time, the observer itself become a suspect. The thing you built to answer "what happened here" become part of what happened here.

A witness that touch the evidence is no longer a witness.

So it watch, it compare, it speak. It never fix. Whoever own the data fix the data — the observer just make sure someone find out in hours, not weeks.

It observe everything. It change nothing. That second half is what make the first half trustworthy.
