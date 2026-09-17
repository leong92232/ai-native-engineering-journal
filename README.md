# AI-Native Engineering Journal

A public journal about building AI-assisted software systems.

Not a code dump. Not a tutorial series. It's a record of the architecture decisions, domain modeling mistakes, and workflow design lessons that come up when you're building real applications with AI doing a growing share of the implementation.

Most of these entries start the same way: something in a real system looked wrong, I dug into why, and the answer turned out to be a boundary problem — state, rules, and execution living in the wrong place.

## Why this exists

AI makes it faster to build features. It does not make it faster to figure out where one system's responsibility ends and another's begins. That judgment call hasn't gotten any easier — if anything it matters more now, because AI will happily build on top of a bad boundary just as fast as a good one.

This journal is where I write that judgment down before I forget why I made it.

## Entries

1. [When a Rule Engine Starts Becoming an App](./01-rule-engine-becoming-app.md)
2. [Approval Is Not a Boolean Flag](./02-approval-is-not-a-boolean-flag.md)
3. [Why Workflow Is Better Than Settings](./03-why-workflow-is-better-than-settings.md)

More entries land as they're written, not on a fixed schedule.

## Recurring themes

- Where deterministic logic ends and AI-assisted judgment begins
- State, rules, and execution — keeping them in the right place
- Domain modeling: when a flag is hiding a missing concept
- Workflow as a first-class thing, not a side effect of settings and conditionals
- What changes about application architecture once AI is doing real implementation work

## A principle that runs through most of it

> AI can help us build features faster. But without clear architecture boundaries, it can also help us create technical debt faster.

## About

Written by [Bruce Lee Jenn Leong](https://github.com/leong92232) — logistics/supply-chain software background, currently focused on AI-native application architecture.
