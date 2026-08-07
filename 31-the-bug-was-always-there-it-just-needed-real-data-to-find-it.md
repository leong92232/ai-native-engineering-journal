# The Bug Was Always There. It Just Needed Real Data to Find It.

Three production errors, three separate days, three separate causes. On paper, unrelated. In practice, the same story wearing different clothes.

One was a type cast on an ID column that worked fine in every test we'd written, and broke the first time it touched a row shaped slightly differently than our test data assumed. Another was a query macro that expanded correctly in every environment we'd tried it in, until it hit our actual production database driver, which handled the expansion differently than we expected. The third showed up only once real records — not seed data, not fixtures, actual rows written by actual use — hit a code path that had been sitting untouched since it shipped.

None of these were introduced by anything we changed that week. That's the part that took a moment to accept. We didn't break them. We just finally ran into them.

The pattern underneath all three: **tested** and **exercised** are not the same word, even though it's easy to let them collapse into one in your head. Tested means the code ran, and the assertions passed, against the shape of data you thought to write. Exercised means the code ran against the shape of data that actually shows up when real use starts throwing real edge cases at it — the malformed row, the unexpected null, the driver quirk nobody read the documentation for.

Tests give you confidence about the inputs you imagined. Production gives you the inputs you didn't.

That gap isn't a failure of diligence. You cannot imagine every real row before real rows exist. The honest version of this isn't "we should have caught it" — it's "this was undiscoverable until the first real data arrived, and now it's discovered." The bug's age isn't the point. Its exposure date is.

What I take from three of these landing close together isn't "write more tests," though that's not wrong either. It's a shift in what "safe" means before a first real rollout: less confidence than the test suite implies, more attention right after real data starts flowing, because that's the actual first real test — the one nothing before it could have run.

> A bug that's always been there isn't a surprise when it appears. It's a delayed appointment, and real data is what finally shows up to keep it.
