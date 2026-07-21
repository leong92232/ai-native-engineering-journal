# Would You Let an LLM Touch Your P&L? Here's Where I Draw the Line

I built an investment analysis system for myself. My own watchlist, my own money on the line. So this question wasn't theoretical for me — it was the first architecture decision I had to make.

AI is everywhere in the pitch decks now. Let the model read the market, let it decide, let it trade. And I do use LLMs heavily in this system. But there's a line in my design, and it's not a soft one.

Anything that touches a number that touches money — is not allowed to be an LLM.

When to buy, when to sell — that's a formula. Plain math on price data. How much — formula. When to exit — formula plus a state machine. Boring, deterministic, the same input give the same output, every single time.

The LLM live in a different layer. It read news, it interpret what's happening in the market, it write me analysis, it challenge my thinking. It's a research analyst, and honestly a good one. But an analyst who advise — never a hand on the trigger. The final decision to actually trade stay with one component only: me.

Why so strict? Not because LLM output is bad. Because LLM output is not repeatable — and everything in the money path must be.

A formula that's wrong is wrong the same way every time. I can backtest it against years of history, find the flaw, fix it, prove the fix. A model that's wrong is wrong differently each time. Ask twice, get two answers. I can't backtest a mood. And when money is lost, "why did it decide that" need a real answer — with a formula, I can point to the exact rule that fired. With a model, the honest answer is somewhere between a shrug and an essay.

There's a simpler way to say all this. Would you accept "the model felt bearish" as a line item explanation in your P&L review? If not, the model doesn't get write access to the P&L.

That's the line, and I think it generalize past trading. Every company is deciding right now which decisions to hand to AI. My rule from building this: hand it the reading, the research, the interpretation, the arguing — the work of understanding. Keep the deciding in something you can replay, audit, and explain — a formula, a rule, or a named human.

Let AI inform the decision all day long.

Just make sure that when the decision is wrong — and someday it will be — you can explain it with something better than "that's what it said."
