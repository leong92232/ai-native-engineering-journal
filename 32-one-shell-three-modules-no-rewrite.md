# One Shell, Three Modules, No Rewrite

We had three separate apps. Each one had its own login, its own navigation, its own way of routing a user around. They worked. They just didn't feel like one system — because they weren't one system, they were three systems that happened to sit next to each other.

The instinct, when you see that, is to rewrite. Tear it down, build the unified version properly, migrate everything at once. It's the version that feels the most correct on a whiteboard.

We didn't do that. We built one shell first — a single login, a single navigation frame, real routing — and left it empty. Then we migrated the three modules into it one at a time. First one, stabilize, confirm nothing broke for the people using it. Then the second. Then the third.

The business kept running the entire time. Nobody had a week where "the system" was half-working because we were mid-rewrite. Each migration was small enough to be boring, which is exactly what you want a migration to be.

Along the way, staged migration caught something a big-bang rewrite would have buried in noise: one module was quietly re-creating a piece of itself on every render, instead of once. In a smaller, isolated change, that stood out immediately — one module misbehaving against a shell that otherwise worked. In a full rewrite, it would have been one bug among hundreds of new lines, indistinguishable from "rewrite growing pains" until someone got unlucky enough to trace it.

That's the actual case for staging it. Not caution for its own sake — smaller change surfaces make real bugs visible instead of camouflaged.

> A rewrite replaces everything at once, so nothing has anything old to be compared against. A staged migration keeps enough of the old system standing that a new bug has no crowd to hide in.

The unified version still arrived. Same destination. But it arrived without ever asking the business to hold its breath for a big-bang cutover, and it arrived having caught a bug the rewrite version of this story probably wouldn't have caught until much later, if at all.

Unify the shell first. Move the pieces in one at a time. Boring is the feature, not the compromise.
