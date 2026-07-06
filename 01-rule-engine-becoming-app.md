# When a Rule Engine Starts Becoming an App

I used to think a rule engine was the answer to many enterprise software problems.

In most companies, business requirements change faster than engineering teams can deliver.

A small rule changes.  
A workflow changes.  
A user wants a new exception.  
A manager wants a new approval path.

If every change has to go through the full development cycle, the team slowly turns into a firefighting team.

That is why rule engines, low-code platforms, BPMN tools, and workflow builders exist.

The need is real.

The idea is simple:

- Let engineers build the core system.
- Let business rules become configurable.
- Let the business team test, review, and improve faster.

A rule engine should be a bridge between engineering and business.

But while building my own automation system, I found a danger:

> A rule engine can slowly become an application.

At first, it only answers decisions.

Given the current state and a set of rules, return a decision.

But then more responsibilities start moving into it.

It starts remembering workflow status.  
It starts tracking who owns the next action.  
It starts managing manual review queues.  
It starts sending notifications.  
It starts waiting for replies.  
It starts behaving like the application itself.

That was the design smell.

The problem was not the rule engine.

The problem was that state, execution, and user intent had moved into the wrong place.

My current principle is:

> The application owns state and execution.  
> The rule engine answers decisions.

The app can ask:

> Given this current state, what should happen next?

But the app should still own:

- Workflow state
- Task lifecycle
- Assigned user
- Audit trail
- Action execution

The rule engine should remain stateless, repeatable, and replaceable.

This separation matters even more in AI-native development.

AI can help us build features much faster.

But if we do not control the boundaries, it can also help us create architectural debt much faster.

A rule engine is powerful when it stays a rule engine.

It becomes dangerous when it quietly becomes the app.
