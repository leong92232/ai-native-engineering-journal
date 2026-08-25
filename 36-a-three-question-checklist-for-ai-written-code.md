# A Three-Question Checklist for AI-Written Code

I don't have a big review process for AI-generated code. I have three questions, and I ask them every time, in the same order.

**Does it do one thing?**

Not "is it long" — length isn't the tell. The tell is whether you can describe what a function does in one honest sentence, without using the word "and" more than once. AI-generated functions pass this less often than they look like they should, because AI optimizes for "handles the request," not "has one job." A function that fetches data, transforms it, and writes a log entry all in one pass looks efficient. It's actually three responsibilities wearing one name, and the moment one of those three needs to change, you're touching code that has nothing to do with the change you're making.

**Does it repeat itself?**

Not just literal copy-paste — the more common version with AI output is *structural* repetition. The same validation logic, written slightly differently, three places in the same file, because each time AI generated the code fresh instead of reusing what already existed two functions up. It's not lazy. It's just how generation works — each answer is self-contained, so it doesn't remember that it already solved this exact problem twenty lines earlier. DRY was always about avoiding two sources of truth that can drift apart. AI makes drift more likely, not less, because it can produce three near-identical implementations in the time it takes a human to write one and copy it.

**Would a stranger understand the name without the comment?**

Read the function or variable name alone, no comment, no context. Does it tell you what it holds, or what it does? AI is fluent at generating plausible names — `processData`, `handleItem`, `result` — that read as reasonable in the moment and mean almost nothing six months later. A name that needs a comment to explain it isn't a documented name. It's a name that already failed, wearing an apology.

None of these three questions are new. They're not AI-specific. That's the point — they're old enough to predate the problem they're now catching. What's different is the frequency you need to ask them. Code review used to happen at human-writing speed, which gave these questions time to breathe. Now the volume is higher, so the questions need to become reflexive instead of occasional — three seconds each, every time, rather than a checklist you pull out for the big changes.

> A function that does one thing, doesn't repeat what already exists, and names itself honestly — that's not a high bar. It's the same bar we've had for decades. AI just made it easier to skip quietly, because the code that skips it still runs.

Three questions. Every time. That's the whole checklist.
