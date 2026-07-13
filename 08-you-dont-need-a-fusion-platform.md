# You Don't Need a Fusion Platform. You Need to Know What Exists First.

Every time I run into a landscape like this — years of country teams and operational teams each building their own tool, loosely connected to a core system, sometimes not connected at all — the instinct is to jump straight to design. Draw the target architecture. Plan the unified platform. Decide what merges into what.

I almost did that this time too.

But I stopped, because I realized I didn't actually know what existed yet. Not really. I knew the core system. I knew a handful of tools by name. I didn't know which business object each one actually touched, which ones were shared, which ones existed for one customer only, which ones nobody outside one country team even remembers building.

You can't design a fusion platform on top of that. You're not designing an architecture — you're designing your assumptions about an architecture.

So I changed the goal for phase one. Not consolidation. Not a target design. Just discovery — record what exists, mostly through automated scanning of databases and deployments, not through asking people to fill in a form from memory. People forget. People also describe things the way they wish they worked, not the way they actually work.

Two disciplines came out of that.

First: keep discovered facts, inferred information, and manually confirmed information separate. A script finding a table is a fact. A script guessing what that table is for is an inference. A person confirming that guess is something else again. Blend those three together and six months later nobody can tell which parts of your landscape map are real and which parts someone typed in once and never checked again.

Second: don't force everything to relate to the core system, as if it's the only thing that matters. Some regional tool touches a business object — an order, a shipment, an invoice — completely independent of the core platform. If your data model can't represent "this tool exists and does real work, and it has nothing to do with the big system," your discovery will quietly bias toward whatever you already assumed was central. You'll find what you were looking for, not what's actually there.

The target architecture can come later. It should come later.

You can't design the future from opinions about the present. You design it from what actually exists — and that has to be discovered, not remembered.
