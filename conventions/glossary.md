GLOSSARY

Version prepared: 10 September 2026, 14:13 BST
Status: IN FORCE from 10 September 2026.

Terms used across this project's documents. Drawn from fourteen
working-practices reports across eleven workstreams and three providers,
then reviewed by four reviewers on 10 September 2026.

Entries record the incident that produced a rule where one exists. Those
are checkable statements rather than decoration.

================================================================
1. WHO DOES WHAT
================================================================

**Operator.** The person who owns the repositories, makes the rulings and
relays artefacts between windows. Every decision that is not mechanical
is theirs.

**Window.** One conversation with one model in one role. Disposable:
windows are replaced when long, and continuity lives in memory and in
committed artefacts rather than in any conversation.

**Workstream.** One repository or project under one orchestrating window.

**Execution agent.** A model with a shell, a filesystem and repository
access, which acts on blocks. It can test an environment claim by
running it, which no reviewer can.

**Reviewer.** A model or person that reads and reports. Has no write
access to the repository and changes nothing.

**Provider.** The company whose model a window runs on. Two windows on
different providers are independent; two on the same provider are not,
however fresh their context.

================================================================
2. ARTEFACTS AND THEIR PARTS
================================================================

**Artefact.** Any file produced for someone else to read or act on. Not
conversation.

**Review artefact.** An artefact composed to be sent to a reader — a
commission, a proposal, a query, a report. Carries an integrity header,
and carries a sign-off request if a reply is expected.

**Repository document.** A maintained file committed to a repository as
part of its content — a convention, a record, a readme. Carries neither
an integrity header nor a sign-off request: the commit fixes its bytes,
and a document that ends by instructing its reader to sign off addresses
the wrong person. Never sent alone; it travels inside a covering
commission that publishes its digest.

A review artefact that is later archived in a repository does not become
a repository document. The distinction is the communicative role, not the
storage location.

**Block.** An instruction file addressed to an execution agent. Anything
addressed to a reader is a commission. The distinction is load-bearing
rather than tidy: a commission pasted into an execution agent gets
reviewed rather than run, which has happened.

**Two-phase block.** A block containing both a read-only assessment phase
and an executing phase, in one file, so that the text assessed is
provably the text executed.

**Bare block.** The block alone, extracted from the wrapper a reviewer
cleared, and delivered to the agent. Extracted mechanically and
hash-verified, never hand-copied — a hand-maintained copy and its wrapper
have drifted silently in practice.

**Wrapper / commission.** The document addressed to a reader, which
contains or accompanies the thing under review.

**Integrity header.** Three lines at the top of a review artefact:
`BODY-SHA256`, `BODY-BYTES`, and a marker line. The digest covers every
byte after the marker.

**Marker line.** `--- BODY BELOW THIS LINE ---`. The **first** occurrence,
at the top of a review artefact, is the marker. A later occurrence is
content — which happens in any document explaining the format.

**Sign-off request.** The closing instruction in a review artefact asking
the reply to end with six items: reviewer, assessed, assessed source
dated, repository, reply ended, verification. The request sits in the
artefact sent; the six items appear in the reply. An attachment sent
inside a covering commission carries the header but not the request.

================================================================
3. PHASES AND CONTROL
================================================================

**Action.** One numbered instruction to the operator at the end of a
reply, carrying exactly one command word.

**Phase A.** The assessment phase of a two-phase block. Leaves the
repository unchanged, may write expressly authorised scratch files,
reports what it found, and always halts.

**Phase B.** The phase that changes things. Runs only on a separate
explicit authorisation in a later message.

**Workstream verification.** A hardcoded check of the remote and, where
the workstream pins one, the branch or baseline commit, run before any
task. If it fails the agent stops and interprets nothing else in the
file. A block may place a paste-integrity guard before it.

**Command words.** ASSESS — read and report, changing nothing, then halt.
RUN — change something. REVIEW — read and report on an artefact. RELAY —
pass an artefact to a recipient. QUERY — put a question. DECIDE — a
ruling is needed from the operator. One per action, appearing once,
never last.

**STOP.** The whole run ends. Reserved for repository-identity failure,
unsafe branch state, unrecoverable tooling failure, or any condition that
makes continuing unsafe. **A stop never reverts, unstages, resets or
deletes anything** — the state is reported and left for the operator.

**HOLD.** One finding only. Work on that finding ceases and independent
work continues; the report states what is missing and why. HOLD sits
inside a run that is still going; STOP ends it. The two were one word
until 10 September 2026, and the ambiguity cost a round: a commission
said both "stop only at the hard stop" and "stop on that finding, then
continue". HOLD is distinct from UNDETERMINED, which is a statement about
evidence rather than about whether work proceeds.

**STATUS / PAUSE / STAND DOWN.** STATUS — report now and keep working.
PAUSE — finish the in-flight step safely, hold new work, keep
subscriptions and triggers armed. STAND DOWN — unsubscribe, disarm every
trigger, stop. Like STOP, none of them ever means deleting or reverting
work.

**HALT.** The designed end of Phase A. Not a stop, and must not be
reported as one.

**Gate.** A condition that must be satisfied before work proceeds.
Distinct from a finding's consequence — see section 6.

================================================================
4. REVIEW
================================================================

**Cold read.** Reading an artefact as someone meeting it for the first
time, with the drafting history deliberately withheld so the reader
discovers where to look rather than being told.

**Lens.** A named question applied to an artefact as a second pass after
a full cold read. An addition, never a substitute — a brief that names a
lens narrows what the reader looks at.

**Round.** One cycle of issue, review and revision.

**Round robin.** One artefact sent to several reviewers at once and
gathered afterwards. Counts as one action, because there is nothing to
choose between.

**Delta review.** Review of what changed since a named point. Clears the
delta only, never the whole.

**Whole-diff review.** A review of the complete diff between an
identified base and a frozen head, with both revisions recorded. Naming
the head alone is not enough: the base determines which changes belong to
the diff. Defects survive several clean delta passes by never being the
line that changed. *Waypoint review* was a second name for this and is
retired — it describes a position in one project's schedule and means
nothing to an outside reader.

**Same-family review.** Reviewer and author share a model lineage. Useful
quality control; not independent review, and cannot authorise
publication or acceptance.

**Independent review.** A reviewer from a different provider, and nothing
else. A fresh session or a new context of the same model is same-family
review. The looser usage is retired: one window watched a same-family
chain converge inside what it called its own echo chamber until a
cross-provider reviewer found two things that chain structurally could
not. **This sense of "independent" is about providers and applies only to
reviewers.** Oracle independence and guard independence, in section 5,
are about derivation and dependency and have nothing to do with
providers.

**Triage.** Judging a finding rather than implementing it. Adopting a
reviewer's prescription wholesale is the same failure as ignoring it.

**Disposition.** The recorded outcome of a finding: adopted, declined,
deferred, superseded. A declined finding stays on the record with its
reason.

**Bot-exhaustion gate.** Running the expensive manual review only after
every automated reviewer has reviewed the current head and its findings
are triaged, and CI is green. Not every reviewer signals approval, so
waiting for approvals rather than reviews waits forever.

================================================================
5. EVIDENCE
================================================================

The labels below describe what an operation established, not merely how
it was obtained. Running a command that does not bear on the claim
does not make the claim verified, and an inference remains an inference
however much extracted evidence supports it.

**Verified by execution.** A command was run and its output directly
establishes the claim. State the command and what it returned.

**Verified by reading.** Established from the text by extraction or
counting, where the extraction directly establishes the claim. State
what was extracted.

**Inferred.** Reasoned from what is present. The reasoning may rest on
extracted or executed evidence; what makes it an inference is that the
evidence does not by itself establish the claim.

**Undetermined.** The evidence was considered and does not settle the
question.

**Unable to verify.** The check could not be performed. State what was
missing — access, a tool, a source. Distinct from undetermined: one is a
conclusion about the evidence, the other about the reviewer's reach.

**Provenance tag.** A per-claim label saying whether something was
fetched or executed this session, is general knowledge not verified now,
or is inference from the text. **Retired** in favour of the labels above;
recorded because earlier reports use it.

**Predeclaration.** Writing down what you expect a measurement to show,
hashing that file, and never editing it. Results go in a separate working
copy — hashing a file you then overwrite proves nothing.

**Oracle.** The source a test's expected value comes from, which must be
derived independently of the code under test. A test that reproduces the
production calculation as its own oracle certifies the defect rather than
detecting it. Independence here means independent derivation, not a
different provider.

**Negative fixture.** A test case built as a genuine baseline plus one
named mutation, with every unrelated field left valid. A negative case
with only the mutated field populated can be rejected by a different
guard than the one under test, so the test passes for the wrong reason.

**Reversion check.** Disable the guard a test names, confirm the test
fails, restore the source byte-identically. A test that stays green with
its guard removed proves nothing.

**Subcase.** One assertion inside a test that contains several. A parent
test failing at its first assertion is evidence only for that one — the
rest never ran.

**Shared defence.** Two guards deliberately producing the same safe
refusal, where each would suffice alone. Distinct from **unique
isolation**, where disabling one guard makes the assertion fail.
Independence here means the guards do not depend on each other, not that
different people or providers wrote them.

**Mutation testing.** Injecting realistic faults and counting how many a
passing suite fails to catch.

================================================================
6. FINDINGS
================================================================

**Finding.** A recorded observation that something is wrong or missing.

**Severity.** How serious a finding is. Recorded as two separate things,
below, because one word cannot carry both.

**Consequence.** What happens if the finding is never fixed. MAJOR — a
wrong outcome that would be acted on. MINOR — a wrong outcome that would
be caught, or a cost without a wrong outcome. NONE — an observation with
no wrong outcome.

**Blocks / does not block.** Whether work may proceed. A separate
question from consequence, and the two come apart constantly: a trivial
defect in text about to be published blocks, and a serious defect in code
about to be deleted does not.

Earlier reports use a single four-value scale — BLOCKING, MAJOR, MINOR,
INFORMATIONAL — in which BLOCKING was a consequence level. It was not;
it was a gate decision. INFORMATIONAL corresponds to NONE.

**Remedy.** A proposed fix, with its own disposition. Rejecting a remedy
never closes its finding.

================================================================
7. DEFECTS
================================================================

**Reference revision.** The named version of an artefact, chosen when its
review campaign opens and recorded with it, against which ORIGINAL and
INDUCED are decided. It changes only by a recorded ruling. Not "the
previous version" — a moving reference lets a restructuring reset every
count.

**Original defect.** Present at the reference revision.

**Induced defect.** Introduced by a change made after the reference
revision. **By fix** — a change made in response to a finding. **By
addition** — a change made to add scope. Only *by fix* enters the bad-fix
rate.

**Bad-fix injection rate.** The proportion of repairs that introduce a
new defect. A term from software-maintenance literature; this project has
no defensibly measured figure of its own.

**Sibling site.** Another place the same thing appears, which a fix
applied at one place misses. The most frequently observed defect
mechanism in this project's review record; not measured.

**Residue.** Text surviving from a superseded design, in a section the
edit never reached.

**Circuit breaker.** A rule that stops patching after a set number of
findings against the same material and requires redesign instead.

**Section cluster.** Repeated findings against one of an artefact's
section headers as they stood at the reference revision, counted from
that revision so a restructuring cannot reset the count.

================================================================
8. STATE, GIT AND PUBLICATION
================================================================

**Present, tracked, committed, pushed.** Four distinct states, and
confusing any two of them has produced a wrong audit. **Present** means
in the working tree. **Tracked** means recorded in the index. **Committed**
means in the repository's history. **Pushed** means available at the
intended remote ref. Only the last is publication.

**Frozen checkpoint.** A named commit against which reviews run, with
nothing in the repository changing underneath for the duration. Half
operator-owned — do not push during an open window — and half
agent-enforceable: pin the SHA and re-verify it against the remote
directly, for example with `git ls-remote`, never by reading a local
tracking ref.

**Commit-pinned URL.** A raw URL containing a full commit SHA, so the
bytes cannot move under a review.

**BASELINE / NEWSHA.** Placeholder words used in blocks for the commit
before a change and the commit it creates.

**Blob id.** Git's hash of a file's content. To catch a filter or
attribute silently transforming content, compare three values: the
unfiltered bytes on disk, the blob as staged, and the bytes on disk
hashed with the applicable attributes. The staged blob already contains
the result of any conversion, so comparing it against itself proves
nothing.

**Default branch.** The branch outsiders see and tooling reads. Findings
on any other branch describe that branch, not the project — a licence
audit reported a project as undeclared when the declaration sat on an
unmerged branch, and the attempt to correct it made the opposite error by
trusting a decision record instead of reading the default branch.

**Staleness.** A remote-tracking ref reflects its last local update,
whether by fetch or by push, and does not establish the remote's current
state. A failed fetch leaves the previous value in place, so read the
fetch's exit code before the ref. In a read-only phase, ask the remote
with `git ls-remote` rather than fetching, because a fetch is a local
write.

================================================================
9. SCOPE AND PROPORTION
================================================================

**Blast radius.** How far the damage reaches if something goes wrong, how
reversible it is, and how many things depend on it. Decides how much
process a task deserves.

**Proportionality.** Matching the weight of the process to the blast
radius. Includes naming when a manual route would be faster than the
agent-orchestrated one, and what the agent route costs.

**Scope freeze.** Only changes that close an existing finding are
permitted. Distinct from a total freeze, which would forbid fixing the
findings that block the work.

**Action ceiling.** The permitted side effects, defined before choosing
tools or architecture. **Prepare-only** is the default for unattended
work: no commit, push, comment, publication or settings change.

**Clean room.** Building from an authorised specification alone, without
consulting a competing product. The rule forbids naming the products
whose design must not leak in; it does not forbid naming the services the
work reads.

================================================================
10. RECORDS AND DOCTRINE
================================================================

**Doctrine.** A repository's binding rules, whatever the file is called.
Every reference to doctrine names the repository, branch and commit it
was read from, because doctrine genuinely diverges by branch inside one
repository: a file described as binding project-wide was found not to
contain decisions a parallel effort was citing from another branch of the
same repository. See section 12.

**Decisions record.** An append-only log of rulings, binding alongside
doctrine. Corrections are marked in place; history is never rewritten to
make an earlier entry look right.

**Correction marker.** A dated note preserving what an earlier entry
claimed and what later evidence changed.

**Completeness claim.** A statement of the form "all X" or "every Y".
Requires a citation resolving to a real, uniquely identifiable check that
exists and is not marked skipped.

**ATX tags.** ATX is this project's artefact-type taxonomy. It assigns
each file a filename suffix — `taskxqz`, `commxqz`, `rptxqz`, `propxqz`,
`instrxqz`, `qryxqz` and others — by what the issuer principally did in
issuing it, not by the subject matter.

================================================================
11. ENVIRONMENT
================================================================

**Harness.** The container and tooling an execution agent runs inside.
Its properties vary between harnesses and are established by probing, not
assumed: whether shell state persists between tool calls, what the
network policy allows, what tools exist. A reviewer without access can
assess reported observations but cannot observe the harness itself.

**Scratch.** A directory outside the repository for probes and throwaway
work. Read-only inspection of the real clone is expected; experiments go
to scratch.

**Capability probe.** A test establishing what a tool can actually do,
using a real resource and a control that does not exist. Models answer
wrongly about their own capabilities when asked in the abstract.

**Egress proxy.** The network policy on an agent's container. Denies some
hosts at CONNECT, which is a different failure from an HTTP error.

================================================================
12. WHAT THIS DOES NOT SETTLE
================================================================

**Where cross-branch facts should live.** Naming the repository, branch
and commit on every doctrine reference makes divergence visible; it does
not remove it. Cross-branch rules living inside per-branch files will
keep producing this, and two windows reached that conclusion
independently — one after finding the divergence by accident, the other
observing that rulings about the order branches merge in live inside
files that cannot see each other. Where such facts should live has not
been decided.

**Terms deliberately omitted.** Named record prefixes, specific rule
numbers and the internal names of particular guards and gates are local
to one workstream and would not help an outside reader. If a merged
practices document needs them, they belong there.
