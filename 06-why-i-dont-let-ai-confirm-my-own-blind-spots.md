# Why I Don't Let AI Confirm My Own Blind Spots

Most time I open AI, I already have an idea in my head. I just want it write nicer, or code it out.

That's fine for small stuff. But I notice something — if I ask it "is this a good idea," it agree with me most of the time. Not because it's true. Because I already frame the question in a way that lead to yes.

Same thing happen with people. You ask your team "you think this plan is ok right?" — most will say yes, especially engineer to a manager. AI do the same thing, just faster, and it don't even mean to.

So I change how I ask.

I stop asking "is this good." I ask it to find where I'm wrong. Push against my own assumption, not confirm it. Heavy research, not heavy agreement.

Example — I was building a document scanner feature, and I had an idea: since people usually place the paper in the center of the frame, why not sample the color at the center, then use that color to flood-fill outward and find the paper's edge?

Sound reasonable to me. So instead of asking "is this a good idea", I ask it to find where this will break in real world, not to help me build it yet.

It come back with three reason, not one. Lighting is not even — center of the paper and edge of the paper can read as two different colors under normal phone camera, so the fill stop early. Center of a real document is usually not blank — it's full of text or a diagram, so the "paper color" I sample might actually be black ink. And if paper color is close to background color (like white paper on white floor), the fill just leak straight into the background instead of stopping at the edge.

None of that I think of myself. I only think about where the paper usually sit, not what actually happen to the pixel value.

Then it showed me the idea isn't wasted — just wrong job. Don't use it to find the edge. Use it to check the edge after some other method already found a candidate: sample color inside the candidate area, if the color is too mixed, penalize it. Same idea, moved to the right place.

This is harder to do than it sound. Confirmation feel good. Correction feel like friction. But the friction is the point.

Same lesson as before, different place this time.

I don't need AI to agree with me faster.

I need it to find where I'm wrong faster.
