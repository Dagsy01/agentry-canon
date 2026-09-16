REVIEWER BEHAVIOUR REGISTER

Version prepared: 13 September 2026, 21:21 BST
Status: IN FORCE from 13 September 2026, ratified by the operator in
    the commit that publishes it.

What each reviewer used in this project can and cannot do, how to brief
it, and the dated observation behind each entry.

**This is a register and it goes stale by design.** Every entry carries
the date it was observed. Providers change models, tools and sandboxes
without notice, so an observation more than a few weeks old should be
re-tested rather than trusted. **An entry with no date is not usable.**

**What belongs here and what does not.** This file holds **capability
facts** — what each reviewer can and cannot do, stated as testable
properties without comparison. **It holds no performance rankings.**
Which provider outperformed which, on what task, at what effort level,
is benchmarking: some providers' terms restrict published comparison of
their service, and a published interpretation that turns out wrong
misrepresents a third party's product. That material lives in the
private companion repository.

**The test for a new observation: does it say what a reviewer is, or how
it ranks?** A property belongs here. A ranking does not. Where an
observation is both, split it and keep only the capability half.

**Why it is here and not in `methods/recurrent-practices.md`.** That
document excluded this material on the grounds that it changes faster
than a convention should. The reasoning was right and the consequence
was not: the knowledge then lived only in individual conversations, and
on 11 September two windows were found holding different assessments of
the same reviewer with nowhere to check either. A register is the place
for something true, useful and perishable.

================================================================
CLAUDE CODE
================================================================

*Observed 8-11 September 2026. Claude Opus 5, CLI in a cloud container
with a shell, filesystem and repository access.*

**What it can do that no reviewer can.** Settle a question from primary
evidence. It holds a repository and can execute, so where others reason
about what a file says, it reads the bytes. On 11 September it measured
31 block files and corrected a claim two windows had been relying on
for two days.

**How to brief it.** Full two-phase blocks, with constants pinned in
advance. **Assign it a lens explicitly** — given a commission whose
lenses were all addressed to other reviewers, it declined to borrow one
and said so rather than improvising.

**Known limits.** Its repository scope is configured per session and it
refuses to read outside it, correctly reporting that as *authorisation,
not capability*. Shell state does not persist between tool calls. Its
clock has agreed with the operator's throughout.

**Behaviour worth knowing.** It stops before irreversible steps and
reports its own deviations rather than absorbing them — on 11 September
it committed correctly, noticed two unauthorised trailers in its own
commit message, and stopped before the push because every correction
was in the block's NEVER list.

================================================================
CHATGPT / CODEX
================================================================

*Observed 8-11 September 2026, as GPT-5.6 Sol and Sol Pro, ChatGPT web
and Work Mode.*

**Strongest at adversarial compliance** — finding the literal reading
that satisfies a rule while defeating what the rule protects. It found a
verification check whose two sides came from one source, a push that
would publish to two repositories while every single-value query showed
one, and a `git fetch` that exits 0 without refreshing the ref it is
read for.

**It executes.** It has a sandbox, runs demonstrations in it, and
reports real output rather than arguing a point. On 11 September it
showed in three lines that a denominator does not make a check honest:
the same 412 lines searched with two patterns give the same denominator
and different answers. It has also run binomial arithmetic against a
threshold claim, and a checksum demonstration proving a self-referential
integrity check passes on either of two different bodies.

**Two reviewers execute, and they execute different things.** Codex
answers *is this reasoning sound* by running it, in a sandbox with no
repository. Claude Code answers *is this true of the repository* by
reading it. **A claim about a general principle goes to Codex; a claim
about a file, a commit or a configuration goes to Claude Code.** Sending
either the other's question gets a correct answer to the wrong
question. An earlier draft of a brief said Claude Code executes "what
the others can only argue about", which is false of Codex; the operator
corrected it.

**Can fetch URLs. Can compute SHA-256. Clock reliable.**

**One caution.** It corrected this project's characterisation of its own
evidence: it had reported *no agreement located*, with its wider search
explicitly failed, and that was recorded as *no agreement exists*. **Take
its limitations verbatim rather than paraphrasing them.**

================================================================
CLAUDE FABLE
================================================================

*Observed 6-11 September 2026, Claude Fable 5.1, claude.ai chat.*

**Strongest at cross-reference integrity and the stranger's-eye read.**
It found a two-report inclusion criterion that was false of all four
entries it admitted — a contradiction four other reviewers missed. It
reads what a document says about itself against what it is.

**Can fetch URLs. Can compute SHA-256. Clock reliable.**

**Its one recurring failure, twice in two days: it reviews against the
version it holds rather than the version that exists.** On 10 September
it raised a finding against a glossary section number that was correct
in the committed file; it had read a superseded draft. **Send it a
commit-pinned URL, not text**, and say plainly which version supersedes
what it may already hold.

**It discloses its own changes of position** — it flagged that it had
passed a clause twice before raising it, rather than letting that look
like a moved goalpost.

================================================================
GEMINI
================================================================

*Observed 9-11 September 2026, web interface.*

**Cannot fetch a URL.** Established by capability probe on 9 September,
confirmed since. **Send it text.** A link is not a delivery.

**Cannot compute SHA-256.** It returns UNABLE TO VERIFY, correctly and
honestly, every time. Do not read that as a failure to engage — it is
the honest answer the three-outcome scheme exists to permit.

**Strongest at omission.** What a document does not decide, what case a
rule leaves unhandled, what a reader would have to guess. It found a
missing definition that two entries depended on, and a placement
question five folder tests could not answer.

**How to brief it.** Ask for what is missing, in numbered separate
questions. Give it the text, never a reference.

**Does not escalate a review tier unprompted.** On 16 September it
reported that an agent lacking full repository context won't
unilaterally raise a tier even when a campaign is mis-scoped, relying
instead on the operator to set it. If the assigned tier may be wrong,
ask it directly rather than relying on it to flag that itself.

================================================================
MISTRAL
================================================================

*Observed 9-11 September 2026, as Mistral Medium 3.5 and GLM in Vibe
Work. **This entry records a disagreement between windows and does not
resolve it.***

**Under a numbered brief with fixed questions per item, it produces
substantial mechanical work.** A complete cross-file claim extraction,
a per-section pass over fifteen sections, and an exhaustive numeric-claim
extraction that caught a false statement in one of this project's own
documents — 46 claims in a file whose own text said none appeared.

**Under an open brief it returns "no defects found."** Twice, on 9 and
10 September.

**Its verification cannot be relied on.** On 10 September it reported
VERIFIED MATCH against a digest belonging to an entirely different
conversation. Its clock has read seven and then nine hours out. On
11 September it reported `sha256sum` non-functional in its sandbox, with
byte counts varying between runs of the same file.

**Its fetch tool returns a 404 page as content** rather than
distinguishing an error from a document. Established by capability probe
on 9 September. **Any URL sent to it must carry a published digest and
byte count**, or it cannot tell a document from an error page.

**A divergent assessment, recorded unresolved.** On 11 September the
PLM PR #13 window reported two tests, two fabricated claims, and
recorded Mistral as not recommended. This window's assessment is the
narrower one above. **The two may be the same behaviour seen from
different angles** — a digest quoted from another conversation is close
to a fabricated claim. Neither assessment has been tested against the
other. **State which you are using when it matters.**

**One later data point, which supports the narrower reading.** On
12 September, under a numbered brief, it returned an accurate
per-section extraction — every cross-reference and numeric self-claim it
was asked to check came back correct — while its own self-reported
digest verification was wrong, traceable to a hashing tool that did not
run in its environment and which it disclosed. **Accurate on the
assigned task, unreliable on its own integrity claim, in the same
reply.**

================================================================
AUTOMATED PULL-REQUEST REVIEWERS
================================================================

*Observed across PLM workstreams, August-September 2026.*

**CodeRabbit.** Rate-limited by push frequency, not by volume. **Trigger
it on demand at a checkpoint, never per push.** Its exhaustion signature
is a warning naming the hourly commit limit and the exact wait time.

**Copilot automatic review.** An automatic per-push reviewer accounted
for more than half of one month's credits in four days before it was
found. **Check what a per-push reviewer costs before enabling it.**

**Codex.** Signals completion in more than one form — a review row, an
issue comment, or a reaction. **Check each reviewer's own evidence form
against the pinned SHA**, rather than one field uniformly across all of
them.

**Qodo.** Hosted signup was blocked for this operator's email address on
9 September; a paid subscription was taken on 11 September. Self-hosted
PR-Agent is Apache-2.0, bring-your-own-key, needs no account, and is
already in this project's Actions allowlist.

================================================================
WHAT THIS REGISTER DOES NOT COVER
================================================================

**Whether any of these reviewers is good.** It records what each does
under what brief. A reviewer that finds nothing under an open brief is
not a poor reviewer; it is one that has been briefed wrongly.

**Anything not observed here.** Absence from this file means nobody
recorded it, not that it does not happen.

**Pricing, limits and model versions.** Those change fastest of all and
are not recorded, because a stale number is worse than none.
