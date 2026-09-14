markdown
# Customs Documents Weren't Built to Be Read by Machines

The instinct, once a team has a working document extraction pipeline, is to point it at everything. Invoices, packing lists, bills of lading, customs declarations — if it's a scanned document with fields in it, run it through the same OCR-plus-model pipeline and populate the database.

For most of those document types, that instinct is fine. A wrong field on an internal packing list gets noticed and corrected, and the cost of the mistake is a few minutes of somebody's time.

A customs declaration is a different category of document, and I think it gets treated as the same category by mistake.

The difference isn't the document's format. It's what happens the moment the extracted data leaves your system. A wrong field on an internal document is a UI problem — something looks off, someone fixes it, nothing outside your walls ever saw the error. A wrong field on a customs declaration is a regulatory submission. It doesn't get "noticed and corrected" before it matters. It matters the instant it's filed, because a government agency now has an inaccurate document with your company's name on it. The cost isn't a support ticket. It's a potential fine, a customs hold, or a compliance flag on a future shipment that has nothing to do with this one.

So the actual question isn't "how accurate is our extraction model." It's "which specific fields on this document carry legal or financial consequence if wrong, independent of how accurate the model is on average." Those aren't the same question, and treating them as the same is where I think teams get into trouble. A model can have excellent aggregate accuracy and still be dangerous, because the handful of fields that matter most — HS code, declared value, country of origin — are exactly the fields where a subtle, plausible-looking error is hardest to catch by eyeballing the output.

I'll name the judgment plainly, because it is one: I think the right response isn't to distrust AI extraction on these documents wholesale, and it isn't to trust it wholesale either. It's to explicitly separate fields by consequence — treat the handful of financially or legally material fields as always requiring a human confirmation step before submission, no matter how confident the model is, while letting lower-stakes fields flow through with lighter review. That's a design choice based on where the risk actually sits, not a finding I can cite a source for.

The honest counterexample here is that most fields on most trade documents genuinely are low-stakes, and gating every single field behind manual review defeats the purpose of automating the pipeline at all. The skill isn't caution everywhere. It's knowing precisely which handful of fields on a given document type are the ones a regulator will actually care about, and reserving the friction for those.

One thing I can't yet claim with confidence: whether a model's stated confidence score is a reliable signal of real error risk specifically on customs-format documents, as opposed to the cleaner document types most extraction benchmarks are built on. I'd want to see that validated before leaning on confidence thresholds alone as the gate. Until then, I'd rather over-include fields for human review than trust a confidence number I haven't tested against this specific document category.

> A hallucinated field in a customer email is an annoyance. A hallucinated field in a customs declaration is a regulatory exposure with your company's name already on it.

The pipeline doesn't need to be slower everywhere. It needs to know which fields it's not allowed to be confidently wrong about.
