REPOSITORY TRAFFIC REGISTER

Version prepared: 15 September 2026, 01:43 BST
Status: IN FORCE from 12 September 2026, ratified by the operator in
    the commit that publishes it. Append-only.

Recorded traffic for this project's public repositories. **One entry
per reading, never edited once written.**

================================================================
0. WHY THIS EXISTS AND WHY IT CANNOT BE RECONSTRUCTED
================================================================

**GitHub retains traffic data for 14 days and no longer.** There is no
archive, no backfill and no API for older periods. A fortnight missed
is a fortnight gone permanently.

That makes this the same class as a review round's findings: **data that
exists in one place for a bounded time and cannot be rebuilt at any
price.** Recording it is cheap; recovering it is impossible.

**Cadence: every 7 days.** Not 14. A weekly reading means one missed
week still leaves the period covered by the next one; a fortnightly
reading has no margin at all.

**No third-party trackers.** Hits, GitTrends, embedded analytics and
badge services all route the request through somebody else's server.
That fails the standing constraint that nothing leaves the operator's
control, and it would also make the repository's own visitors visible
to a party nobody chose.

================================================================
1. HOW TO TAKE A READING
================================================================

  1. Open the repository, then **Insights → Traffic**.
  2. Record every field in section 3's schema, from the page.
  3. Add the entry to section 4. **Never edit an earlier one.**

**Two caveats that change how the numbers read**, and both should be
remembered when anyone interprets them later:

  **Your own views are excluded while you are signed in.** The figures
  are other people, not you — which is what makes them worth recording
  and also means they will look lower than any impression formed from
  using the repository yourself.

  **Clones include automation.** A CI job, a scheduled fetch or an
  agent session cloning the repository counts as a clone. Clone figures
  are not a readership measure.

================================================================
2. WHY THIS IS PUBLIC, AND THE ONE THING TO WITHHOLD
================================================================

**Public, because this repository's discipline is do not claim,
measure.** These figures are the record of what the hosting platform
reported, kept where anyone can check it — and keeping a record private
while publishing conclusions drawn from it would be the wrong way round.

**They are not evidence that anything was read.** Section 5 states the
limit and it governs: a view is a page load, a clone is often
automation, and every artefact this project circulates points at raw
URLs that appear here not at all. **Nothing in this register supports a
claim about readership or use**, and a claim of that kind would need a
different measurement that this project does not have.

The figures are the operator's own, about the operator's own
repository. No third party's performance is being measured and nothing
is being compared, so none of the reasons that keep other registers
private applies.

**The exception: referrers can expose someone else's private space.**
The referrer list shows where visitors came from. A visitor arriving
from a private forum, an internal tool, a paid community or an unlisted
page puts **that** URL in Insights — and publishing it would expose a
location that is not the operator's to publish.

**So: check every referrer before writing it down.** Where one is a
private, internal or unlisted location, record it as `private referrer,
withheld` with its count. **The count is the useful part; the URL is
the part that is not yours.**

**The caveats in section 1 are part of the record, not preamble.** A
view count published without them is an invitation to misread it.

================================================================
3. THE SCHEMA
================================================================

One block per reading, per repository:

    REPOSITORY   the full name
    READ ON      the date and time the reading was taken
    PERIOD       the window the page reports, as it states it
    VIEWS        total
    VISITORS     unique
    CLONES       total
    CLONERS      unique
    REFERRERS    top sources as listed, with their counts — each
                 checked before recording; a private, internal or
                 unlisted source is written `private referrer,
                 withheld` with its count retained
    CONTENT      most-visited paths as listed, with their counts
    NOTES        anything that would change how the figures read — a
                 link posted somewhere, a mention, a scheduled job
                 added or removed

**Record a zero as a zero.** An empty field is ambiguous between "none"
and "not looked at", and this register is worthless if a later reader
cannot tell those apart.

**Record the period as the page states it**, not as you infer it.

================================================================
4. READINGS
================================================================

    REPOSITORY   Dagsy01/agentry-canon
    READ ON      12 September 2026, 23:40 BST
    PERIOD       last 14 days, as the page states it — the charts span
                 29 August to 12 September 2026
    VIEWS        26
    VISITORS     1
    CLONES       73
    CLONERS      39
    REFERRERS    github.com — 5 views, 1 unique visitor
                 (the only entry listed; nothing withheld)
    CONTENT      /branches — 7 views, 1 unique
                 Overview — 5 views, 1 unique
                 /tree/main — 5 views, 1 unique
                 /tree/main/conventions — 5 views, 1 unique
                 /blob/main/conventions/review-le… — 3 views, 1 unique
                 /blob/main/conventions/reviewer-… — 1 view, 1 unique
    NOTES        First reading. The repository's first commit was
                 7 September 2026 and all charts read zero until
                 6 September, so this period covers essentially the
                 whole of its existence.

                 One unique visitor against 26 views. Own views are
                 excluded while signed in, so that visitor is not the
                 operator. Every content row shows 1 unique visitor,
                 consistent with a single party browsing several pages
                 rather than several parties arriving.

                 39 unique cloners against 1 unique visitor is the
                 striking figure and it is almost certainly not 39
                 people. Clones include automation, this project runs
                 agent sessions that clone the repository, and the
                 clone series begins on 6 September — when that work
                 began. Treat the clone figures as this project's own
                 tooling unless something distinguishes them.

                 Referrer github.com with 5 views is internal GitHub
                 navigation, not an external link.

================================================================
5. WHAT THIS DOES NOT MEASURE
================================================================

**Anyone who read the files without visiting the repository.** Every
artefact this project sends points at `raw.githubusercontent.com`
rather than the repository page, and raw fetches do not appear in
Insights → Traffic at all. **The windows this project tells to fetch
the canon are invisible here by design.**

**Whether anything was read.** A view is a page load.

**Why anyone came.** The referrer list is the closest available and it
is a list of sources, not reasons.
