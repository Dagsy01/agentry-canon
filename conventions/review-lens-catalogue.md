REVIEW LENS CATALOGUE — FOR SPECIFICATION AND GOVERNANCE DOCUMENTS

Version prepared: 10 September 2026, 09:54 BST
First issued: 9 September 2026, 16:59 BST, as v01.
For: the conventions repository, as a standing catalogue to select from
From: the Claude Chat audit window, after eight versions and one external
    round-robin on a product specification
Version: v07
Status: IN FORCE. Ratified by the operator, 9 September 2026, and
    committed to conventions/ on that basis.

REVISION HISTORY. One paragraph per version, newest first, so no line is
edited in place.

v07 — removes the `Repository: none. Pull request: none.` line, which is
review-artefact apparatus that contradicted the committed status and has no
meaning in a repository document. Rewords section 6 items 6 and 7, which both
said "Once" while mandating three lenses twice.

v06 — drops the self-certifying provenance claim in favour of a bare
version date, after the carried-forward line failed for the third time;
extends H3 with that third instance and the reasoning for taking its
second branch. Corrects the section 7 heading, which still said COMMITTING
after 7.2 became a statement of form.

v05 — ratified and committed. Corrects the status, which declared the
document unratified while placing it in a folder of conventions in force.
Replaces the committing instruction at section 7.2, which described a
stripping that had already been done and duplicated a rule the sign-off
convention already carries, with a pointer to that convention.

v04 — regenerates the provenance line, which had been carried forward from v01
across two revisions and therefore asserted a freshness it no longer had.
Extends H3 with that failure mode. Reflows this note into one paragraph per
version, after the previous form acquired a wrap artefact from its own fix.

v03 — corrects the revision note, which said v01 gave the wrong count in two
places when it gave it in three, and extends A3 with the case-sensitivity
caution that produced that error.

v02 — corrects the lens count, which v01 gave as forty in three places and
which is forty-one. Removes the applied-versus-unused audit that was section 7,
because reporting what happened on one document is a different communicative
act from prescribing how reviewers work, and a dated audit inside a standing
convention is a staleness trap. Adds the committing instruction at section 7.
Classification confirmed as ATX-001 instrxqz by ruling of 9 September 2026,
17:02 BST.

================================================================
0. WHAT THIS IS, AND THE TRAP IT CARRIES
================================================================

Forty-one lenses that can be applied to a document which specifies something
someone else will build. It is a menu to select from, never a checklist to
complete.

**The trap, recorded before the list because it has already cost a round on a
related project.** Naming a lens narrows what a reviewer looks at. A brief that
named specific letters of a typeface produced reviews that assessed those
letters and nothing else — the named thing became the whole scope. So:

  1. **A lens is an addition to a full cold read, never a substitute for one.**
     Every commission must say so, and must ask for cold-read findings first,
     under their own heading, before the lens pass.
  2. **Assign few lenses per reviewer.** One is usually right; two is a
     maximum. A reviewer given six will do six shallowly.
  3. **Running all forty-one is not thoroughness, it is theatre.** Section 6
     gives a selection rule.

================================================================
1. GROUP A — THE DOCUMENT AGAINST ITSELF
================================================================

  A1  **Internal consistency.** Does any section contradict another? The
      highest-yield lens on a revised document.
  A2  **Residue.** Does anything survive from a superseded design? Ask what was
      removed, then hunt for it.
  A3  **Sibling-site completeness.** For every fix, was it applied at ALL its
      sites? Mechanical: search for the old phrasing. Reading back does not
      catch this, because you see what you meant.
      **Make the search case-insensitive, and search for the shortest
      distinctive stem rather than the whole phrase.** A case-sensitive search
      silently misses a sentence-initial occurrence and returns a confident
      undercount; a whole-phrase search misses any occurrence broken by a line
      wrap. Both failures have occurred in this campaign, one of them in the
      revision note of this document.
  A4  **Traceability.** Does the change record match the document? Does every
      claimed fix exist where it claims to be?
  A5  **Terminology discipline.** Is one thing called one name throughout? A
      second name for the same thing becomes a second thing in the build.
  A6  **Cross-reference integrity.** Do all internal pointers resolve, and to
      what they claim? Check numbering and lettering sequences.

================================================================
2. GROUP B — THE DOCUMENT AGAINST ITS READER
================================================================

  B1  **The builder with no author.** Implement it exactly, ask nobody. What
      gets built that the author did not intend?
  B2  **Silence.** What does it not decide? For each gap, what would a
      reasonable builder do, and does that breach anything?
  B3  **Ambiguity.** Where could two competent readers diverge and both be
      defensible?
  B4  **Prerequisite ordering.** Can the work be done in the order implied, or
      does something depend on a decision made later?
  B5  **Assumed expertise.** What does it assume the reader already knows, and
      is that assumption safe for the intended implementer?
  B6  **Proportionality.** Is the document heavier than the thing it specifies?
      Over-specification produces compliance theatre and hides the load-bearing
      rules among the trivial ones.

================================================================
3. GROUP C — ADVERSARIAL
================================================================

  C1  **Malicious compliance.** Satisfy every sentence literally while
      producing something the author forbids. The single most valuable
      adversarial lens.
  C2  **Lazy compliance.** The cheapest implementation that technically passes
      every acceptance criterion. Different from C1 and often more realistic.
  C3  **The hostile reader.** Someone looking for a defence for a shortcut they
      have already decided to take. What does the document hand them?
  C4  **Threat model.** What is worth attacking here, what would an attacker
      gain, and does the document address it?
  C5  **Third-party abuse.** Not the builder and not an attacker — how could a
      legitimate user, or the vendor of a service being read, misuse what this
      specifies?

================================================================
4. GROUP D — VERIFICATION
================================================================

  D1  **Acceptance-criterion testability.** For each: what exactly would a
      person do to test it; could two testers disagree; is it a criterion or an
      aspiration?
  D2  **Falsifiability.** Can each requirement fail? A requirement that cannot
      be failed is a wish.
  D3  **Measurability.** Are quantities defined with units, sources and
      precision? "Recent", "quickly", "small" are defects.
  D4  **Arithmetic.** Recompute every worked example. Errors here are cheap to
      make and expensive to inherit.
  D5  **Observability.** Can the built thing be checked from outside, by
      someone who did not build it?

================================================================
5. GROUP E TO H
================================================================

**E — External constraints.**

  E1  **Terms of service.** Does anything specified breach the terms of a
      service it touches? Development and testing count, not just what ships.
  E2  **Licensing.** Of every dependency, and of the product itself. Engine and
      rules can carry different licences; internal-use restrictions bite on
      redistribution.
  E3  **Platform and store policy.** Single-purpose rules, permission
      justification, disclosure requirements, obfuscation bans.
  E4  **Data protection.** What personal data is touched, on what basis, with
      what retention? Third parties' data, not only the user's.
  E5  **Accessibility.** Colour-only signalling, keyboard reachability,
      screen-reader behaviour. Almost always missing from a first draft.
  E6  **Jurisdiction and vendor constraints.** Where does data go, and does that
      satisfy the operator's own standing rules?

**F — Lifecycle.**

  F1  **Failure and degradation.** Every error path, partial data, and what the
      user sees.
  F2  **Migration and upgrade.** What happens to existing users' data on
      update?
  F3  **Uninstall and end of life.** What is left behind, and where?
  F4  **Staleness.** Which claims will age? Are they dated? A survey finding
      stated as a permanent fact is a defect.
  F5  **Maintenance burden.** What breaks when a third party changes something,
      how visibly, and who notices?

**G — Scope and product.**

  G1  **Scope coherence.** Does every requirement serve the stated purpose, or
      are there orphans from an earlier scope?
  G2  **Non-goals integrity.** Is anything required that a non-goal forbids?
  G3  **Differentiation survival.** Do the stated differentiators survive the
      requirements, or does a constraint quietly kill one?
  G4  **Cost of compliance.** What does each rule cost to satisfy, and is any
      rule more expensive than the problem it prevents?

**H — Process, specific to a multi-agent campaign.**

  H1  **Clean-room contamination.** Does anything describe HOW rather than
      WHAT, at a detail no requirement needs?
  H2  **Claims discipline.** Every public claim the document instructs the
      product to make, checked against what the product actually does.
  H3  **Provenance and integrity.** Headers, digests, and whether the artefact
      can be identified after it travels.
      **Check every provenance line against the version it now sits in.** A
      line that was true when written becomes false by being copied forward,
      and a stale timestamp asserting its own freshness is worse than one that
      says nothing, because it forecloses the check. Regenerate such a line on
      every version, or state the version's own date and drop the claim about
      how it was produced. This failure occurred in this document three
      times — v01's line carried through two revisions, then v04's carried
      into v05 despite the correction — which is why this document now
      takes the second branch and states its date without certifying it.
      A line that claims nothing about its own freshness cannot be false
      about it.
  H4  **Convention compliance.** Against the operator's own filename, footer
      and reporting rules.

================================================================
6. SELECTION RULE
================================================================

Do not run all forty-one. Choose by what the document is and what has changed.

  1. **Always, on any version after the first:** A1, A2, A3. Contradiction,
     residue and sibling-site completeness are where revision defects live, and
     A3 is mechanical rather than a matter of judgement.
  2. **Always, before any external round:** B1 and C1. If a literal implementer
     can build the wrong thing, nothing else matters yet.
  3. **Whenever acceptance criteria exist:** D1.
  4. **Whenever a section is NEW and has never been externally reviewed:** give
     it a lens of its own. New sections carry the defects.
  5. **Whenever the scope changed:** G1 and G2.
  6. **Before anything is built:** the whole of E. These are the lenses whose
     findings cannot be fixed later without discarding work.
  7. **Again before publication:** E3, E4, E5, H2. Deliberately a repeat of
     three lenses from item 6: platform policy and data-protection law move
     between building a thing and releasing it, and an answer established at
     the start may not hold at the end.

Diminishing returns are real, but the figures behind that claim are one
observation from one document by one author and are NOT a result. They are
recorded in the separate audit artefact, not here, and must not be cited from a
convention as though the convention established them.

================================================================
7. CLASSIFICATION, FORM, AND STATUS
================================================================

**7.1 Classification: ATX-001 `instrxqz`, ruled 9 September 2026, 17:02 BST.**
The subject matter is a catalogue and a catalogue is reference, but the
principal communicative act is prescriptive: section 0's three rules and
section 6's selection rule bind every future commission. The forty-one entries
are the vocabulary those rules operate over, not the act. ATX-001's own test
settles it — a reviewer briefed next month must comply with "a lens is an
addition to a cold read" whether or not they have seen this campaign.

**7.2 Form.** This file is a repository document. It was circulated for review
as a review artefact carrying an integrity header and a sign-off footer, and
both were stripped for commit. The rule governing that distinction lives in
`conventions/reviewer-sign-off.md` and is not restated here.

**7.3 Status.** IN FORCE from 9 September 2026. Section 0's three rules and
section 6's selection rule bind every commission written after that date. The
applied-versus-unused audit that was section 7 of v01 lives as its own
artefact, because a dated report of one document's review history is a
different act from a standing instruction and would otherwise go stale inside
one.
