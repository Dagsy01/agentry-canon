RUNNING A WHOLE-DIFF REVIEW

Version prepared: 12 September 2026, 22:42 BST
Status: IN FORCE from 12 September 2026, ratified by the operator in
    the commit that publishes it.

This file spans `methods/` and `briefs/` on its own reading: it says how
to carry out an act (running the review round) and it also says what to
ask of the artefact under review. Rule 3 of
`conventions/repository-structure.md` permits keeping a file that spans
two folders together, on the specific condition that the halves depend
on each other — and they do here: the lens and closure-audit mechanics
in section 3 only make sense alongside what a round is actually asking
of a reviewer, and separating the two would mean either duplicating
that context in two files or leaving one half unable to stand alone.
Kept together for that reason, it stays in `methods/` rather than
`briefs/` because the act is the harder-won part — what to ask of a
diff is largely restated from existing per-provider registers; how to
actually get several reviewers to answer a coherent question about the
same artefact, without the round collapsing into noise or silently
omitting a file, is not written down anywhere else this document's
author could find. (Rounds run so far have used five; nothing below
depends on that specific count, and it is reported as what happened,
not prescribed as a size.)

================================================================
1. WHAT THE ACT IS, AND WHEN IT HAPPENS
================================================================

A whole-diff review is the last check before a merge decision on a pull
request that has already been through incremental, ambient review
(automated bots reviewing each push as it lands). It answers a different
question than incremental review can: not "does this latest change look
right," but "is the complete, cumulative proposal — read as one thing —
sound." The two questions have different failure modes. A defect
introduced once and never touched again survives an unbounded number of
clean incremental passes, because it is never the line that changed in
any of them.

Run it once the ambient reviewers available on the artefact have all
reported on the current head, and before authorising a merge.

================================================================
2. PRECONDITIONS, AND WHAT A MISSING ONE COSTS
================================================================

**A frozen head, read live and confirmed, not assumed.** Every reviewer
in the round needs to be looking at the same commit. On one round this
document's author commissioned, the actual base chosen for "the whole
diff" was wrong — an intermediate commit from partway through the day's
work, not the pull request's real base against its target branch. The
result: the generated diff silently omitted one of four changed files
entirely, and every reviewer in that round would have reviewed a
three-file proposal believing it was the whole one, had the omission
not been caught before the round was sent. The fix, once caught, was
comparing the pull request's own reported base (from the hosting
platform's PR object) against the commit the review request had used,
rather than trusting an earlier session's memory of "the starting
point." **The rule this implies, stated plainly rather than left in the
incident alone: if the live base disagrees with what the commission
pinned, the round is void before it starts — record both values and
stop, rather than proceeding on either one by assumption.**

**Every reviewer seeing the SAME artefact, not a related one.** A
reviewer that has been used earlier in the same day, on the same
project, may hold context from an earlier round and answer against
that instead of what it is actually sent this time. State explicitly,
in the commission itself, what supersedes anything the reviewer might
already be holding.

**A known standard to judge against**, stated in the commission, not
left for each reviewer to infer. What counts as a finding, what is
already settled and should not be re-raised, and what is explicitly out
of scope for this round.

**Pinning the two endpoint commits does not, by itself, specify which
diff to generate between them.** A reviewer applying an adversarial
lens to an early draft of this method constructed a throwaway
repository where a target branch and a proposal branch had each
advanced separately from a common ancestor. Holding the exact same two
endpoint commits fixed, a direct two-endpoint comparison and a
comparison from the common ancestor produced two different, both
internally consistent, both independently verifiable artefacts — one of
which presented an unrelated change on the target branch as though it
were a deletion proposed by the pull request. Both can be given a
correct digest; both pass every check section 2 and section 3 describe;
only one is the actual cumulative proposal a whole-diff review is
meant to examine. **State explicitly, in the commission, which
comparison form was used to generate the diff — the form measured from
the common ancestor of the two branches, not a direct comparison of
their tips — and confirm no name for the two forms is being used
interchangeably.**

================================================================
3. THE MECHANICS, AS ACTUALLY RUN
================================================================

Four terms recur below with a specific meaning: a **commission** is the
document sent to reviewers requesting the round; the **operator** is the
person running the round and making its decisions; a **window** is one
reviewer's individual session; a **block** is an instruction file
written for an executing agent to carry out, distinct from a
commission, which asks for judgement rather than execution.

**One file, not one per reviewer.** The first attempt at a round in
this project sent a separate file to each reviewer, differently worded
per recipient. The operator running the round pointed out directly that
this required matching the right file to the right window by hand,
which is real friction for a human doing the pasting, and a source of
mis-routing risk (the wrong file reaching the wrong reviewer). The
corrected form: one file, with a shared section stated once at the top,
followed by a clearly labelled section addressed to each reviewer by
name. The same file is pasted, unchanged, into every reviewer's window.
Each finds its own section and may ignore the rest.

**What the shared section must state, learned by omission.** An early
round of this shape omitted several things a later reviewer pointed out
were missing, each of which had cost a round: the artefact's own digest
and byte count (without which a reviewer cannot tell a genuine copy
from a truncated one — and at least one reviewer's own fetch tool has
returned a 404 page as page content without erroring, making this a
real risk, not a theoretical one); what has already been found and
closed in prior rounds (without this, reviewers re-raise settled
findings and a round is spent confirming rather than finding); the one
thing most wanted from the round, stated plainly, since a round with no
stated target returns everything and ranks nothing; what is explicitly
out of scope; and an instruction to state plainly when nothing is
found, since without it a reviewer with nothing to report can invent
something rather than say so.

**A digest cannot be inline in the document it identifies.** A first
attempt at stating "this document's own digest" wrote the value
directly into the document's own text — which cannot verify, because
computing the digest changes the bytes the digest was computed over.
The corrected convention: two lines and a marker at the very top of the
artefact —

    BODY-SHA256: <digest of every byte after the marker line>
    BODY-BYTES: <count of those bytes>
    --- BODY BELOW THIS LINE ---

— built by hashing the body first and prepending the three lines
afterward, never the reverse. The digest then covers everything below
the marker and nothing above it, which makes the check self-contained.
Exactly what "every byte after the marker line" means, so two people
computing it get the same number: the count begins on the character
immediately following the marker line's own newline, and includes the
artefact's own final newline if it has one. Give the literal command
used, not a description of what it does, since a description leaves
room for two people to draw the boundary differently and both be
confident.

**This convention applies to an artefact travelling on its own for
review — never to a document whose destination is being committed to a
repository.** A repository-bound document carries no header of its own
kind at all: once committed, the surrounding repository's own version
control is what establishes its identity, and a header inside the file
would be redundant with that. Such a document is instead sent, while
still in review, inside a covering message that itself carries the
three-line header and states the enclosed document's digest and byte
count on its behalf. This document is itself in that second category —
it carries no header of its own, correctly, and whatever transmits it
for review should state its digest in a covering message rather than
inside it.

**One lens per reviewer, none repeated, chosen for what each reviewer
demonstrably does well rather than assigned uniformly.** A round giving
every reviewer the same open "review this" brief converges reviewers
toward the same class of finding and leaves gaps nobody was asked to
look at. Rounds run this way have produced several genuinely distinct,
non-overlapping findings each time — this is the observation the
practice rests on, not a controlled comparison against the alternative,
and it is reported at that strength rather than as a proven superiority.
**An earlier, narrower practice on the same project required the
opposite: every reviewer in a round given the identical single lens,
rotated between rounds, specifically so a finding could not be
attributed to the reviewer or the lens ambiguously.** This document
recommends the newer practice on the strength of what it has since
produced, but the two have not been run side by side on the same
artefact, and a reader adopting either should know the other was tried
first and abandoned on evidence, not on a controlled trial. The lens is
additive to a full cold read, stated as such in the commission — never
a substitute for one, since a reviewer that only applies its assigned
lens will miss anything outside it, including things an unguided read
would have caught.

**A returning reviewer — one that has already reviewed an earlier
version of the same artefact — gets a closure audit instead of a fresh
lens.** For each finding it previously raised: is it closed, partly
closed, or reopened in the current version. A finding it cannot locate
as any of the three is itself a reportable result. This depends on the
returning reviewer and the commissioner agreeing on what "each finding"
is — in practice, on findings being numbered once, by whoever raised
them, with the commission quoting those exact identifiers rather than
assigning its own. Where that precondition held, this approach has
surfaced findings a fresh cold read would have had to rediscover from
nothing; it is reported as promising rather than as a settled
comparison against a fresh lens on the same reviewer.

**A finding and its proposed remedy are judged separately.** A reviewer
correctly identifying a real defect, and then offering a fix for it,
are two different claims — accepting one does not obligate accepting
the other. In one round, a reviewer's own suggested one-line patch for
a defect it had just found was tested before being applied, and it
reopened a different, more serious hole in the same file: the finding
was entirely correct; the fix, tested, was not. Had the fix been
applied on the strength of the finding being right, the round would
have made the artefact less safe while believing it had made it safer.

================================================================
4. WHAT WENT WRONG
================================================================

**A reviewer's fetch tool has returned a 404 page as page content, not
an error.** This means an "I have read the document" response from
that reviewer cannot be trusted without an independent digest check —
the reviewer may be reporting confidently on a 404 page's text believing
it to be the artefact. Send the full text directly rather than a link
wherever this is a live risk, and require the digest check every time.

**A reviewer has answered "no defects found" under an open, unscoped
brief, and produced substantial, specific findings under a numbered
brief with a fixed question per item, on the same underlying material.**
The difference was entirely in how the round was structured, not in
the reviewer's capability. Where a reviewer's output quality is known
to depend heavily on question structure, structure the questions.

**A document that had been rewritten from top to bottom because its
central claim was found unsupported still carried a stale internal
cross-reference to content that no longer existed after the rewrite**,
pointing a reader at "the rationale below" when the section it meant
had been replaced. Neither the author nor the first round of review
caught this; a second, independent pass did. Superseding text in place
does not, by itself, catch every pointer into the superseded material —
each needs checking separately. This is a specific case of a broader,
already-published rule: successive incremental review can omit a
defect introduced once and never touched again, because it is never the
line that changed (`methods/recurrent-practices.md`, section 10). The
stale cross-reference is what that rule looks like when the defect is
a pointer rather than a line of logic.

**A ratified rule, applied and committed the same day it was ratified,
was found by three separately-run reviewers — working independently,
without coordination — to fail open in five distinct ways**, none of
which had been anticipated when the rule was drafted. The rule's own
justification for existing was that it was mechanically verifiable and
hard to game; independent convergence on five separate gaps, found the
same day, was direct evidence that justification had not held for the
verification mechanism actually used (a text-pattern filter over
source code, rather than anything that understood the code's actual
structure). The rule was withdrawn rather than patched, on the
reasoning that a mechanism whose entire claimed value was "hard to
game" should not be kept and incrementally re-patched against each new
way it was shown to be gameable — that is the wrong shape of fix for a
rule making that particular claim.

================================================================
5. THE NEAR-MISSES
================================================================

**An authorisation instruction asked for something the person giving it
could not actually supply.** A rule required exact technical text
"supplied verbatim by the operator" before a consequential action could
proceed. The operator's own reply did not supply that text — it
delegated ("use whatever the default would be") rather than stating it.
The executing agent correctly treated the delegation as not satisfying
the rule's literal requirement, and stopped rather than either
proceeding without the text or inventing something to fill the gap.
Nothing was lost; the near-miss is that the rule, as originally
written, demanded something structurally impossible for the person
subject to it to provide, and this was only discovered by hitting it
live. The fix was not to relax the rule but to change who supplies the
value: for anything only the executing side can actually know, have it
state the exact value in its own report, so the other party only ever
confirms rather than composes unknown content from nothing.

**A base-branch mismatch was caught by a mechanical check that existed
for an unrelated reason.** A block designed to compare two commits
included, as a matter of standing practice rather than because this
specific risk was anticipated, an explicit live comparison against the
target branch's actual current tip before proceeding. That check firing
is what caught the wrong-base error described in section 2 — not
because anyone suspected the base was wrong, but because verifying
live, mechanically, rather than trusting a value carried in from
earlier, is applied as a blanket habit regardless of whether a specific
risk is suspected in the moment. The near-miss is how easily this
particular check could have been treated as boilerplate and skipped
under time pressure, given nothing in that block's stated purpose
flagged base selection as a risk.

================================================================
6. WHAT COULD NOT BE DONE, AND WHY
================================================================

Coverage claims from any single round of this kind are bounded by three
things, stated so a reader can judge how much weight the round's "no
findings" carries: whether every reviewer actually read the complete
artefact rather than a partial fetch (at least one round's reviewer
explicitly reported reading a subset of changed files, and said so
plainly rather than implying full coverage — this should be the norm,
not the exception, and a round should ask for the count explicitly);
whether a reviewer's own execution environment could reach every
resource the review needed (one reviewer's environment could not reach
a specific external registry needed to settle one question, and
reported this as an explicit limit rather than guessing past it); and
whether the review round's own commissioning correctly scoped what was
being asked, since a well-run round against a badly-scoped question
produces confident, useless answers.

================================================================
7. WHAT IS STILL UNSETTLED
================================================================

**What happens when two reviewers, both independent and both careful,
reach opposite severity judgements on the same finding.** This project
has hit this directly — one reviewer treating a demonstrated gap as
blocking, another treating a structurally similar gap as an accepted,
disclosed limitation consistent with the artefact's existing design
philosophy. Both readings were defensible from the same evidence. No
rule in this project currently says how that disagreement resolves
short of a project owner deciding it case by case, and it is not
obvious a general rule could say more than that without losing
something real in each specific case.

**Whether a lens-assignment scheme scales past the number of
genuinely-distinct lenses a given set of reviewers can usefully be
assigned.** Every round run so far has had enough reviewers and enough
plausible lenses that "one each, none repeated" was achievable. What to
do once there are more reviewers than distinct lenses worth assigning
is untested.

**How much a returning reviewer's closure audit should be trusted when
the artefact has changed enough that "closed, partly closed, or
reopened" no longer cleanly describes what happened to a given finding**
— for instance, when a fix for one finding changes the code in a way
that makes an earlier finding's original framing no longer quite apply,
without the underlying concern being resolved either. This has not yet
produced a clean answer in this project's own experience.

================================================================
8. FIXED VALUES FOR THIS METHOD ITSELF
================================================================

This method does not name a specific repository, branch, head, or tool
version, because it is written to be run against any artefact meeting
section 1's description — those values belong in the commission for a
specific round, not in the method describing how to run one. What a
specific commission must pin, per this method: the artefact's own
digest and byte count, with the exact boundary command used (section
3); the exact base and head commits being compared, and the comparison
form used to generate the diff between them, confirmed live against the
hosting platform's own record of the pull request's base, not carried
forward from an earlier session (section 2); which reviewers are in the
round and which lens or closure-audit role each has been assigned; what
has already been found and closed, stated explicitly rather than left
implicit; the one thing most wanted from the round; what is explicitly
out of scope; and the instruction that a reviewer finding nothing must
say so plainly. This list repeats every item section 3 already names as
required, in full — an earlier version of this section quietly kept
four of seven and dropped three, which is the exact failure this method
exists to prevent, recurring inside its own summary.
