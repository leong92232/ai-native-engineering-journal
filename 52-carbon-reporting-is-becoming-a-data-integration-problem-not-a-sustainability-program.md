# Carbon Reporting Is Becoming a Data Integration Problem, Not a Sustainability Program

Most companies still staff carbon reporting the way they staff a sustainability program.

A policy lead. A few analysts. A consultant on retainer for the annual disclosure.

That team writes the narrative, sets the targets, and files the report.

It made sense when the number on the page was mostly Scope 1 and 2 — fuel burned, electricity metered, numbers that live inside the company's own systems.

But the ground has shifted.

CBAM enters full enforcement in 2026. CSRD is pulling Scope 3 into the same disclosure as Scope 1 and 2, under the same assurance standard. And Scope 3 does not live inside your systems. It lives inside your suppliers' systems, your carriers' systems, your customers' systems — hundreds of them, in different formats, different units, different levels of digital maturity.

That is not a sustainability problem. That is an EDI problem wearing a sustainability label.

I have seen this shape before. It's the same shape as CargoIMP and EDIFACT twenty years ago: one company needs a fact that only exists in another company's system, and there is no shared contract for how that fact gets handed over.

The current default handling of Scope 3 makes this worse instead of better. Most companies fill the gap with spend-based proxies — dollars spent on steel, converted to an emissions estimate by an industry average factor. It is not measurement. It is a placeholder standing in for a fact nobody collected.

CBAM changes the incentive structure on this directly. From 2026, unverified estimates get replaced by punitive default values. Suppliers who can provide actual, third-party-verified data suddenly become more valuable trading partners than suppliers who can't. The emissions number stops being a footnote and starts being a procurement filter.

Once that happens, the sustainability team can't own this alone. This becomes a question of: who is the reader, what is the fact, and what is the contract for handing it over.

- The reader is whatever system collects a supplier's actual activity data — kilograms of steel, liters of fuel, kilowatt-hours — not the analyst reformatting a PDF by hand.
- The rule is the calculation methodology — GHG Protocol, ESRS category mapping, CBAM's own installation-level formulas — applied consistently to whatever facts come in.
- The app is whoever owns the resulting number, tracks its provenance, and can explain six months later where it came from and why it's defensible under audit.

Right now, most organizations collapse all three into one spreadsheet and one team. That works until the volume of suppliers, the diversity of formats, and the assurance requirement all show up in the same year — which for CBAM-exposed importers, is this year.

The sustainability team should still own the target and the narrative. But the data pipeline underneath it — supplier onboarding, format normalization, verification tracking, audit trail — is an integration architecture problem, and it should be resourced like one.

Carbon reporting didn't get harder because the climate math changed. It got harder because the number of external systems you now depend on for a single disclosure line multiplied, and most companies never built the contract layer to handle that.
