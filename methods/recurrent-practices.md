RECURRENT PRACTICES

Version prepared: 11 September 2026, 02:44 BST
Status: IN FORCE from 11 September 2026, ratified by the operator in the
    commit that publishes it.

Fourteen working practices that recur across separate windows' records,
and one added afterwards from a single window and marked as such.
Each is stated with the rule, how many reports carry it, what
independence evidence exists for it, and the incidents behind it.

**Which folder test this file meets, and why**, as
`conventions/repository-structure.md` section 4 rule 3 requires of a
file that spans two. It meets `methods/` — how to do a thing: worked procedures
and working practices, each with the incident that produced it. The
rules are methods; the incidents beneath them read as `registers/`
material. They are not split, because the incident is the evidence for
the rule, and a rule separated from its evidence is a bare assertion
that gets dropped the first time it is inconvenient.

**This document was called CONVERGENT PRACTICES until 10 September
2026, and claimed that separate windows had arrived at these rules
without seeing each other's records. Four reviewers found that claim
unsupported, and two blocked publication on it. It is withdrawn.** What
the evidence shows is recurrence. Whether any rule was independently
discovered is not established, and section 0 says why.

================================================================
0. WHAT THE COUNTS ARE, AND WHAT THEY ARE NOT
================================================================

On 10 September 2026 one brief went to every window then running.
Fourteen reports came back from eleven workstreams across three
providers, covering four pull requests on one repository, two other
repositories, and three projects with no repository at all. Roughly two
hundred practice entries.

**A count below is the number of reports stating the rule. It is not a
number of independent discoveries, and nothing here establishes that
any rule was discovered more than once.**

One person relays artefacts between every window. A rule agreed in one
conversation reaches another by that route without either window
knowing it happened. So a rule in six reports may have been discovered
once and repeated five times.

Two observations are sometimes offered against that — that a rule
appears with different incidents behind it, or in reports from
different providers. **Neither establishes independent discovery.**
Different incidents can be applications of one transmitted rule.
Different providers can receive the same relayed material. Both are
recorded per entry below as facts about the reports, not as arguments.

**What recurrence is worth without independence.** Recurrence
establishes that several separate reports state the practice. It does
not establish that any window followed it, or how consistently —
reports can repeat an intention, an instruction or a copied policy.
Whether a rule is actually kept would need evidence of execution, and
none is offered here. That is a weaker claim than the one v1 of this
document made, and it is the one the evidence supports.

Each entry carries an **Independence evidence** line stating what is
actually known: how many reports, whether the incidents behind them
differ, and whether provider information was recorded. Where it says
"not stated", that is the honest answer and not an omission.

**On the inclusion threshold.** Entries appear here if two or more
reports carry them, with one marked exception at section 15, admitted
at the operator's instruction; the five with exactly two are marked as
such. The earlier criterion admitted
two-report entries only where the two "reached them by visibly
different routes" — which was false of all four such entries, each of
which describes two windows making the same error and applying the same
correction. That criterion is withdrawn. The five two-report entries
are kept and marked, and a reader can discount them accordingly.

================================================================
1. A REVIEWER'S FINDING IS EVIDENCE, NEVER AN INSTRUCTION
================================================================

*Independence evidence: five reports; four distinct incidents; two of
the three providers.*

Verify a reviewer's claim against the live artefact before acting on
it, and judge the proposed remedy separately from the finding. Adopting
a prescription wholesale is the same failure as ignoring it.

The four incidents differ. One reviewer's named remedy for a serious
defect would have deadlocked by construction — two operations sharing
one queue, one called from inside a lock the other must wait on.
Another's first remedy would have silenced a false message while
leaving the orphaned resource it was reporting. A third proposed
specific numeric thresholds to make a vague rule testable: the finding
was right, the numbers were invented, and adopting them as written
would have presented arbitrary constants as though evidence had
selected them. A fourth twice treated a rule file's own confident
comment as if it were a settled disposition.

**A rejected remedy never closes its finding.** The finding stays open
until an acceptable remedy, a recorded acceptance of the risk, or
another disposition addresses it.

================================================================
2. VERIFY MUTABLE STATE AT THE MOMENT IT MATTERS
================================================================

*Independence evidence: six reports; two of the three providers;
whether the incidents differ is not stated.*

Do not carry state forward from when a block was written. Re-read the
exact head, branch, thread or dependency immediately before a mutation,
and again before the final report.

**On what to do when it has moved.** Stop, unless the block itself
defines what legitimate advance looks like. Where a branch advances
under a process the block knows about, the check is that the
commissioned head is an ancestor of the current head *and* the
intervening commits come from that process — ancestry alone is not
enough, and exact equality refuses correct work. Where the block
defines no such allowance, any movement is drift and the run stops.

An earlier version of this entry said "stop on drift rather than
reconciling it", which three reviewers found contradicted by the
incident beneath it: the incident describes exactly the case where
stopping is wrong.

**What no report says is how to resume.** A reviewer raised this twice
and it is recorded rather than answered: none of the six reports
describes what happens after a stop — whether the work restarts from
its assessment phase against the new state, or the operator reconciles
by hand. Both were observed; neither was written down as the rule.

================================================================
3. A TEST THAT STAYS GREEN WITH ITS GUARD REMOVED PROVES NOTHING
================================================================

*Independence evidence: two reports; two distinct incidents; providers
not stated.*

Disable the guard a test names, confirm the test fails, restore the
source byte-identically. One window calls this the highest-yield
practice in its whole set.

Two routes, not three. One window found roughly forty tests green for
the wrong reason: a later schema change had made their fixtures invalid
on unrelated grounds, so the guard each claimed to test could be
deleted with the suite staying green. Another reached it from
negative-fixture construction — a skeletal negative case gets rejected
by a different guard than the one under test.

**A third report was previously counted here and has been removed**, on
two reviewers' finding: the rule that a test must not reproduce the
production calculation as its own oracle is a different practice, and a
copied oracle is not in general exposed by removing a guard. It is
recorded below as related rather than as support for this one.

**Related rules that travel with this one.** Count assertion subcases,
not finding headings — a parent test failing at its first assertion is
evidence only for that assertion, because the rest never ran.
Distinguish unique isolation from shared defence: where two independent
guards deliberately produce the same refusal, removing both
manufactures a failure without proving either bites. And derive a
test's expected value independently of the code under test.

================================================================
4. A UNIVERSAL CLAIM NEEDS EVIDENCE THAT RESOLVES
================================================================

*Independence evidence: two reports; same route — both had already made
the error; providers not stated.*

"All producers", "every call site", "the race is closed", "all findings
discharged" — each requires a citation resolving to a real, uniquely
identifiable check that exists and is not marked skipped. Otherwise the
claim is written instance-scoped.

One window records several occasions in two days where a record claimed
coverage the code did not deliver, most of them caught by an external
reviewer rather than the author. The rule was then tightened when a
reviewer pointed out that a syntactically valid reference to a test
that was never written would pass the first version of it.

================================================================
5. PREDECLARE AND HASH BEFORE MEASURING, IN TWO FILES
================================================================

*Independence evidence: two reports; same route — both wrote the rule
the same way first and both corrected it the same way; providers not
stated.*

Write down what you expect a measurement to show, save it outside the
working area, hash it, and never edit it. Observed results go in a
separate copy.

Both windows first wrote the rule as one file to be filled in as
results arrived, and both corrected it because hashing a file you then
overwrite proves nothing. One reports the rule proving itself
immediately — a predeclared conclusion was refuted by its own probe,
and because the prediction was fixed the refutation was visible instead
of quietly absorbed.

**Unhandled, and stated rather than hidden:** where an expected value
cannot be known in advance — a timestamp, a generated identifier, a
model's output — neither report says what to predeclare. Predeclaring
the *test* rather than the value is the obvious answer and no report
records it as practice.

================================================================
6. HARNESS PROPERTIES ARE PROBED, NOT ASSUMED — INCLUDING WHETHER
   SHELL STATE PERSISTS
================================================================

*Independence evidence: three reports; incidents differ in detail;
providers not stated.*

Establish what an execution environment actually does before relying on
it. In the harnesses these reports describe, shell state does **not**
persist between tool calls, so a value needed later must be used in the
same call or re-stated as a literal in the next, and the same applies
to the working directory. That is a property of those harnesses, not of
agent tool calls in general.

One window found it by probing its own harness after five full external
review rounds had missed it, because the defect exists only at the
level of execution. Blocks had been passing variables between separate
fenced snippets, which would have produced a silent, exit-zero,
zero-byte result.

An earlier version stated the non-persistence as the rule and the
probing as a note. Two reviewers found that a reader on a harness where
state does persist would discard the entry and lose the general form,
which is the part that transfers.

================================================================
7. A HASH IS A FINGERPRINT, NOT A DISCLOSURE REVIEW
================================================================

*Independence evidence: two reports; same route — both required full
readback first and both corrected it when an artefact grew; providers
not stated.*

A digest establishes that bytes match a value you already trust. It
establishes nothing about whether those bytes are the right ones.
Approving a hash without reading what it covers does not show the
intended text was written.

Both windows first required complete readback, and both corrected it
when an artefact grew too large: full terminal output became a
truncation risk in itself, making the verification channel less
reliable than the file. The corrected rule reads full artefacts back
and checks large ones by whole-file digest plus bounded structural
inspection.

**Where the boundary sits is not settled and no report gives a
threshold.** Two reviewers found that "small", "large" and "bounded"
cannot be applied consistently as written, and that a reader who
misjudges hits the truncation risk the rule exists to avoid.

*Editorial proposal, not reported practice: each block declares its own
boundary — full readback below a stated size, and above it a digest
plus a stated number of leading and trailing lines with a line count.
No source report describes this; it is offered because the gap is real
and marked as an addition so it is not read as gathered.*

**And the two are different questions.** A digest comparison answers
identity. What content review the bounded inspection stands in for is a
separate matter the reports do not settle.

================================================================
8. CORRECT AN OVERSTATEMENT IN PLACE; NEVER REWRITE HISTORY
================================================================

*Independence evidence: two reports; same route — both from records
claiming test coverage that did not exist; providers not stated.*

When a record turns out to have claimed more than shipped, mark the
correction with its date and preserve the original wording. Do not edit
an earlier entry to make it look right.

One window reports the practice earning its place when the same failure
recurred one level up and the second correction marker could point at
the first.

================================================================
9. SAME-FAMILY REVIEW IS NOT INDEPENDENT REVIEW
================================================================

*Independence evidence: three reports; incidents differ; providers not
stated.*

A fresh session or a new context of the same model is useful quality
control. It cannot authorise acceptance, and a merge gate must not rest
on it. The terms are those ruled in `conventions/glossary.md`:
**same-family** for a different context of the same model,
**independent** for a different provider.

One window iterated with a same-family reviewer across four rounds to a
clean pass, then brought in a cross-provider reviewer, which reported
two defects the preceding rounds had missed — in that window's words, a
syntactical echo chamber the chain had converged inside. **That is a
report of what happened, not proof that the earlier chain could not
have found them**; later discovery by another reader does not establish
incapacity, and one reviewer found the stronger claim unsupported.

The corollary is separately reported and stands on its own:
**agreement is not authority.** Two models agreeing is evidence.
Authority comes from the owner or from a policy defined in advance.

================================================================
10. A WHOLE-DOCUMENT READ ALONGSIDE DIFF REVIEW
================================================================

*Independence evidence: three reports; incidents differ; providers not
stated.*

Successive incremental diffs can omit a defect introduced once and
never touched again, because it is never the line that changed. Build
at least one whole-document read into any long iterative sequence
before final execution.

A stale self-referential version label survived three consecutive clean
diff-based passes, and two reviewers doing a fresh whole-document read
each caught it immediately. The same mechanism explains why a residue
check performed by diff misses a term surviving in sentences the edit
never reached — a search for the old wording finds those even
where the incremental diff omits them.

The limit is specific to *incremental* review. A single diff spanning
the introducing change would contain it.

================================================================
11. LIVE ACCESS CATCHES WHAT TEXT REVIEW STRUCTURALLY CANNOT SEE
================================================================

*Independence evidence: four reports; incidents differ; providers not
stated.*

Where correctness depends on facts about a real system, get a
report-only check from the agent that can read it, before spending
review rounds on wording built atop assumptions.

Eight rounds of careful textual review never caught that a block
targeted the wrong base branch, because the fact was not in the text a
reviewer had. A scheduled run had no `gh` command at all, so a whole
block built around it had to be rewritten. A parser silently omitted
data a downstream library required unless a flag was passed.

**The limit is about what evidence the reviewer holds, not about
reading.** Any of those facts could have been established by reading if
someone had supplied the environment's actual state. One text-only
reviewer stated the limit about itself, unprompted: it can catch what
is wrong in the text, not what is wrong about the system it has not
been shown.

================================================================
12. THE FIRST PAGE IS NOT COMPLETE EVIDENCE
================================================================

*Independence evidence: three reports; incidents differ; providers not
stated.*

When a conclusion depends on every thread, comment, run or file,
retrieve every page and state the resulting count.

One window built a capability matrix from page one alone and omitted
sixty-five later comments, producing a false silent failure, a false
gap in the timeline, and a false conclusion about a reviewer's
behaviour. Another notes that a persistent comment edited in place
keeps its original position in creation order, so it can sit on an
early page while its content is hours newer.

================================================================
13. GREEN IS NOT PROOF
================================================================

*Independence evidence: three reports; incidents differ; providers not
stated.*

A green job, a passing suite, or a reviewer's silence is not evidence
of correctness. Inspect the actual output.

A successful workflow run contained an HTTP 404, a secondary error in
its own logging, and a discrepancy between its configured model and the
one that answered — and still published its outputs and completed
green. A reviewer's persistent comment said clean while its own review
object carried a finding. Another's check run was green while its last
comment referenced a stale commit.

**Silence is the sharpest case**, because it is indistinguishable
between "nothing to report" and "reviewing something else". Missing,
pending, stale, errored and silent are five states and none is a pass.

================================================================
14. TIMESTAMPS COME FROM A CLOCK, AT THE MOMENT OF WRITING
================================================================

*Independence evidence: five reports; incidents differ; providers not
stated. Three of the five record breaching the rule themselves.*

Never estimate a timestamp, carry one forward, or type one from a
reading taken earlier. Derive it in the same operation that uses it.

One window traced the mechanism rather than the symptom: bare `date`
returns UTC in at least one container and gets hand-transcribed as
local time, producing an identical one-hour error three times running.
Another got filename stamps wrong repeatedly by taking a reading and
then typing it, and corrected the rule to say that taking and typing
are not the same as deriving, because the gap between them is where the
error lives.

**The corollary is stronger than the rule.** A stale timestamp that
asserts its own freshness is worse than one that says nothing, because
it forecloses the check. Where regeneration keeps being forgotten, drop
the claim rather than repeating the instruction.

================================================================
15. TRIAGE BY WHAT CANNOT BE RECOVERED
================================================================

*Independence evidence: one report — this window, 11 September 2026.
It does not meet this document's inclusion threshold and is included
anyway, marked, at the operator's instruction. Discount it accordingly.*

**Order work by whether it can be reconstructed if lost, not by whether
it feels urgent.** A thing that can be rebuilt from public facts on any
future day is never the priority over a thing that exists in one
conversation and nowhere else.

The incident is this campaign, on 10 and 11 September 2026. A set of
fourteen practices, cleared by four reviewers at 15:38, sat uncommitted
for eleven hours while the same window ran licence audits across three
repositories, drafted website copy, chased a product name spelling and
investigated a page that turned out not to be wrong. Every one of those
was recoverable at any time from public information. The uncommitted
material was not, and roughly a hundred and sixty single-window
practices gathered the same day are still recoverable only from one
conversation.

**The test is one question: if this conversation ended now, could this
be rebuilt?** If yes, it waits. If no, it is the next thing done. A
licence declaration can be written any day; a round robin's findings
cannot be reconstructed at any price once the window closes.

**Two corollaries.** Committing is preservation, not ceremony — an
artefact in a repository at a pinned commit survives everything, and one
in a conversation survives nothing. And a window that notices it is
doing recoverable work while irrecoverable work waits should say so
rather than finish the task in hand first.

================================================================
16. WHAT IS NOT HERE
================================================================

**Practices reported by only one window.** Roughly a hundred and sixty
entries appear once, many of them specific and hard-won, and several
will turn out to be general once another workstream meets the same
problem. They are held in the full corpus, except the one admitted at
section 15 and marked there. One reviewer notes the cost:
a threshold that prioritises recurrence over coverage will exclude
single-report practices describing rare but severe failures.

**A rule for resolving conflicting findings between reviewers.** One
reviewer identified this as the gap the collection implies and does not
fill: these fifteen entries assume several reviewers producing
substantial findings, and nothing here says what happens when two
independent reviewers contradict each other or propose mutually
exclusive remedies. No report supplies one.

**Numbers, and what the ones here are.** The counts of reports are
counts made when this document was assembled. **Every other figure in
this document — how many tests were green for the wrong reason, how
many comments were omitted, how many rounds missed something — is
reproduced from a source report and has not been independently
verified.** They are incident details, not measurements, and no
validated performance rate is claimed anywhere. Proportions do appear
where a report gave one — section 14's "three of the five", section 4's
"most of them" — and they carry the same status as every other figure
here: reproduced, not verified. An earlier version claimed no figures
appeared at all, which four reviewers found false.

**Nothing about how to work with a particular model or tool.** Those
change faster than a convention should.
