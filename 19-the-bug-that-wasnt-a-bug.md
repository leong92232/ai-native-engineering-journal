# The Bug That Wasn't a Bug — It Was a Missing Ownership Rule

Config values in my system kept changing when nobody changed them. That was the report I filed against myself: settings I set through the web app, later showing up different. Classic bug. Somewhere, something is overwriting.

So I trace it. And I find it fast — the backend engine was writing into the configuration table. Directly. Confidently. With code I wrote myself, months earlier, that was working exactly as written.

Here's the uncomfortable part. The web app also write that table — that's its job, it's where users edit their settings. The engine writing there wasn't malicious or even careless. On the day I wrote it, it was the shortest path: engine compute something, engine save it, done. Locally reasonable. Each module, looked at alone, doing nothing wrong.

Which mean I couldn't actually call it a bug. A bug is code violating the intent. But I had never declared the intent. Nobody ever decided who own that table. There was no rule to break — and that was the defect.

Two writers, one table, no owner. The "bug" was just the day the two writers finally disagreed.

And I want to point at something here: I built both modules. Alone. People think boundary violations need two teams that don't talk. No — one person on two different days is enough. Me-in-March made an assumption, me-in-June made a different one, and neither wrote it down, so there was nothing for the second one to violate.

The fix took two forms. The small one: move the write, engine no longer touch that table. Ten minutes. The real one: declare the rule that was always missing — every table has exactly one writer. The web app own configuration; if the engine compute something worth saving, it save it in its own territory, or hand it to the owner and let the owner write it. Reading is open. Writing is owned.

That rule now do something the patch alone never could: it turn future violations into actual bugs. Next time something write where it shouldn't, there's a declared intent to point at. The violation become visible, nameable, catchable in review — instead of sitting quietly for months as two reasonable pieces of code waiting to disagree.

The lesson I keep from this one: when you find a "bug" where every piece of code is doing its job correctly, stop looking for broken code. Look for the rule nobody wrote down.

Some bugs you fix with a patch.

This kind you fix with a sentence — written down, where the next version of you will find it.
