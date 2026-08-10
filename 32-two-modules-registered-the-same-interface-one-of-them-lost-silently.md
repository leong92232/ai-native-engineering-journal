# Two Modules Registered the Same Interface. One of Them Lost, Silently.

Two parts of the system needed a database connection. Each one registered its own, independently, both against the same interface.

Nobody planned for that collision. Nobody needed to — right up until the moment it mattered.

Dependency injection doesn't ask which registration you meant. It resolves to whichever one registered last. No error. No warning. No log line saying "heads up, two things wanted this slot, picking one." It just quietly wires everything downstream to whichever module happened to load second, and moves on like nothing happened.

We didn't find this in a test. We found it in production, when one module's queries started returning data that belonged to a different part of the system. The queries weren't wrong. The connection they landed on was.

That's the part worth sitting with. Everything about the code, read in isolation, looked correct. The bug wasn't in any single line — it was in an assumption neither module knew it was making: *I am the only one who registers this.* Both modules held that assumption. Only one of them got to be right, and the deciding factor was load order, not intent.

Load order is not a design decision. It's an accident that happens to be deterministic enough to hide behind.

The fix wasn't complicated once we saw it: stop registering by interface alone, and require an explicit key for each registration. Now "which connection wins" is a decision someone makes on purpose, visible in the code, instead of an accident of which file happened to import first.

> Silent precedence is not a resolved conflict. It's an unresolved one that hasn't been noticed yet.

What stays with me isn't the bug itself — bugs happen. It's how confidently wrong the system looked while it was happening. No error state. No degraded mode. Just two reasonable pieces of code, each individually correct, producing a wrong answer together because the framework picked a winner nobody asked it to pick.

If two things can register the same interface, that's not a coincidence waiting to happen. It's a decision you haven't made yet, made for you, by whichever one loads last.
