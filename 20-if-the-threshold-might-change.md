# If the Threshold Might Change, It Belongs in the Rule Engine

After I built my own rule engine, a funny thing happen: I start seeing rules everywhere.

Every if-statement look like it should be externalized. Every status change look like it deserve a configurable rule. When you own a hammer, the whole codebase look like nails. And I know from the other direction how bad it get — I've written before about a rule engine slowly becoming an app. This is the same disease, opposite side: an app outsourcing its own spine to the rule engine, one if-statement at a time, until nobody can read the app and know what it does.

So I needed a line. Where does a decision belong?

The case that settled it for me: I'm building a learning app. Student submit answer, AI grade it, and there's a confidence score attached. The question — above what confidence does the AI's grading stand on its own, and below what does a human teacher have to review it?

Two decisions, sitting right next to each other in the same feature:

The flow itself — submitted, then graded, then maybe reviewed, then returned. That's a state machine. It change only when the product change, which mean when the code change anyway. Externalizing it buy nothing. It stay in the app.

The threshold — is 0.85 the right bar? That number is different. Operations will want to tune it. Someone will want to try 0.9 for one subject and 0.8 for another. Someone will want to A/B test it against teacher workload. That number will change for business reasons, at business speed, by people who should not need a code deployment to change it.

That's the line. Not "is this logic important" or "is this logic complex" — but: **who change it, why, and how often.** Change with the code, by engineers, when the product change — keep it in the app. Change for business reasons, by business people, at business speed — that's a rule, put it where rules live.

And here's the part people over-estimate: the cost of externalizing one decision. This integration is about fifteen lines. One call — here's the score, should a human review? One answer. And one fallback: if the rule engine is unreachable, default to the safe side, send it to human review. No workflow sync, no callbacks, no shared state. The app still own everything — it just ask one question it doesn't hardcode the answer to.

Most decisions in an app never need to leave the app. The state machine is the app.

But a threshold someone will want to tune next quarter, buried in code where only a deployment can touch it — that's a business decision held hostage by an engineering process.

Set it free. Just that one. Not everything.
