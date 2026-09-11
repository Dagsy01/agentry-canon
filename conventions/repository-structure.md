REPOSITORY STRUCTURE

Version prepared: 11 September 2026, 02:44 BST
Status: IN FORCE from 11 September 2026, ratified by the operator in the
    commit that publishes it.

Where a file goes in this repository, and the test that decides it.

================================================================
1. WHY THIS EXISTS
================================================================

Five folders were agreed on 9 September 2026 and never committed. On
10 September a document was proposed for the wrong one, and the reason
was traceable: an uncommitted test is a conversation rather than a
rule, and a reader cannot check it.

This file makes the tests fetchable. Every later placement question is
then a recorded ruling against a published text instead of a fresh
argument.

**A folder without an occupant yet is a stated plan, not a broken
link.** No count of which folders are populated appears here: any such
count is false from the commit that changes it, including the commit
that publishes this file.

================================================================
2. THE FIVE FOLDERS
================================================================

**`conventions/` — how we name, tag and structure things.**
Naming schemes, artefact taxonomies, the sign-off format, this file.
Rules about the form of things rather than about how work is done —
including the required form of an artefact that directs work, such as a
block or a commission. The procedure for using one belongs in
`methods/`.

**`methods/` — how to do a thing: worked procedures and working
practices, each with the incident that produced it.**
A procedure for one task, such as committing a licence file; or a set
of practices that govern how work is carried out. Both carry the real
instance behind them.

**`briefs/` — how to review a given kind of thing.**
What to ask of a specification, a block, a set of test fixtures. The
lens catalogue's selection rule points at material of this kind.

**`registers/` — what happened and what was decided.**
Dated records with no rule attached: campaign logs, audits, rulings
digests. A register goes stale by design and says so; a convention or a
method does not.

**`convergence/` — how to tell whether the process is working.**
Classification schemes for defects, thresholds, and the measurements
that would show whether review is converging or circling.

================================================================
3. THE `methods/` TEST WAS WIDENED, AND HERE IS THE RECORD
================================================================

As agreed on 9 September, `methods/` read: *how to do a thing — worked
procedures, each with a real instance.*

**On 10 September 2026 it was widened to include working practices**,
so that it now reads as section 2 states. The occasion was a document of
fourteen practice rules, each with the incident behind it, which fitted
no folder cleanly: the rules read as `methods/`, the incidents as
`registers/`, and splitting them was rejected because the incident is
the evidence for the rule and a rule separated from its evidence is a
bare assertion.

A sixth folder, `practices/`, was considered and rejected. It would
have overlapped `methods/` so heavily that nobody could predict which
held what, and an unpredictable structure is worse than a slightly
widened test. **If the remaining single-window practices turn out not to
fit `methods/` when they are merged, that is the moment to reconsider —
with the material in hand rather than in advance.**

This change is recorded rather than absorbed because a widened test
that nobody can see is indistinguishable from a test being ignored.

================================================================
4. HOW TO APPLY THE TESTS
================================================================

  1. **Ask what the file principally does**, not what it is about. A
     document about reviewing is not automatically a brief; a document
     about naming is not automatically a convention. The subject matter
     is the weakest signal available.
     This is the artefact taxonomy's own test in different words — tag
     by the communicative act, not by the subject matter — applied to
     placement rather than to naming. They are one rule and should stay
     one.
  2. **A file goes in exactly one folder.** Where two tests both seem to
     fit, the question is which act the file principally performs.
  3. **Where a file genuinely spans two**, do not split it if the halves
     depend on each other. State which test it meets and why, in the
     file.
  4. **Where no test fits**, that is a finding about the tests. Record
     it and rule on it; do not file the document somewhere approximate
     and hope.

================================================================
5. COMMITTED FILES THESE TESTS PLACE ELSEWHERE
================================================================

**No count appears in this heading.** An earlier draft said "one" and
was wrong within a day, which is the same failure section 1 forbids for
folder populations and section 4 of `methods/recurrent-practices.md`
forbids for universal claims.

**`conventions/review-lens-catalogue.md`**, committed on 10 September
2026, is a catalogue of review lenses with a rule for selecting among
them — which is `briefs/` by the test in section 2, *how to review a
given kind of thing*, and not `conventions/`.

**`registers/recurring-block-patterns.md`** reads the same way. It
describes itself as a checklist for reviewers to check new drafts and
findings against, which is the `briefs/` test again; the `registers/`
test it now sits under is *dated records with no rule attached*, and ten
standing rules are neither dated nor a record. **It was placed there by
a ruling of 10 September 2026, before these tests were committed.** That
ruling stands until it is changed, and whether the file moves again is
open rather than decided here.

**The catalogue is in `conventions/` because that was the only folder
that existed when it was written.** This is recorded rather than fixed
by quietly widening `conventions/` to cover it, for the reason section 3
gives: a test bent to fit an existing file stops predicting anything.

**Ruling: the catalogue moves to `briefs/` when that folder is
created.** This ruling is about `conventions/review-lens-catalogue.md`
only. The checklist above is not covered by it.

The move of `recurring-block-patterns.md` to `registers/` was ruled by
the operator on 10 September 2026 and executed on 11 September in commit
`e9c0663596d7e142f50ffbcee4195a720e0b429c`, with both digests recorded
in `registers/recurring-block-patterns-digests.md`. An earlier draft of
this section said that move was not agreed; it was true when written and
was overtaken before this document was committed. The lens catalogue's
move remains outstanding and no longer shares a commit with it.

**Who creates `briefs/`, and when.** The folder is created by the
commit that first places a file in it — git has no empty folders — so
this move is what creates it, and no separate authorisation to create a
folder exists or is needed. It requires the same two-phase block any
commit here requires.

Existing commit-pinned URLs for the catalogue are unaffected: they name
a commit **and** a path, and the old path still resolves inside the old
commit. A move changes where the file is found in later commits, not in
earlier ones.

Until then, a reader looking for review briefs should look in
`conventions/` and `registers/` as well.

================================================================
6. WHAT THE FOLDERS DO NOT COVER
================================================================

**The repository root** holds repository-level files only — `README.md`
and `LICENSE` — and nothing else. A file at the root that is not one of
those is misplaced. Without this a reader applying rule 4 raises a
finding about the tests for every root file, which is not what rule 4
is for.

**Templates and blank forms** have no folder, and three reviewers'
worth of test-application did not place one. A template is not a rule
about form, not a worked procedure, not a brief, not a record and not a
measurement. **Ruling: a template lives beside the thing it is a
template for**, and is named so that it reads as one. If templates ever
outnumber that arrangement's usefulness, they get a folder then.

**Research and case-study material** — a written account of a campaign
for readers outside this project — is **out of this repository's
scope**. This repository holds the conventions and methods a project
runs on. A study of how they worked is a different artefact for a
different audience, and giving it a folder here would invite the
repository to become both.

================================================================
7. WHAT IS NOT DECIDED HERE
================================================================

**Depth.** No rule says whether a folder may contain subfolders. None
does today, and the question has not arisen.

**Where cross-branch facts live.** Recorded as unsettled in
`conventions/glossary.md` section 12. Doctrine that must hold across
branches currently lives inside per-branch files, which has already
produced one real misunderstanding. A repository-level home for such
facts is needed and has not been chosen.

**Whether the root `README.md` should describe this structure.** It
currently carries the licence notice alone.
