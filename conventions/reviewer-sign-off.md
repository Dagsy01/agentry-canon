# Reviewer sign-off

Every reply from a reviewer — human or model — should identify what
produced it, what it assessed, and when. Without that, a record of a
review round is a set of anonymous opinions, and whoever compiles it
reconstructs the provenance by hand from the order things arrived in.
That reconstruction is slow and it has already gone wrong.

This convention exists so that nobody has to remember it. **The
requirement travels inside the artefact being reviewed**, so that
sending the artefact carries it. Nothing is appended by the person
running the round.

## Two kinds of document

The rules below apply differently to each, and conflating them produces
a file that violates its own instructions.

A **review artefact** is composed to be sent — a commission, a
proposal, a query, a comment, a method under review. It carries the
integrity header at the top and the sign-off footer at the end.

A **repository document** is a file committed to this repository. It
carries neither. Its bytes are fixed by the commit, so a commit-pinned
URL supplies what the header would; before commit, the covering
commission's published digest serves the same purpose. And a convention
that ended by instructing its reader to sign off would be addressing the
wrong person.

Because a repository document carries no header, **its digest is taken
over the whole file** — every byte, from the first. That holds even when
the document's own text contains something that looks like a marker
line, as this one does where it explains the header format below.

**A repository document is therefore never sent on its own.** It is
sent inside a covering commission, which is a review artefact and
carries the header and footer on its own behalf, publishes the
document's digest and byte count, and states the document's date. A
repository document sent alone arrives with no sign-off instruction at
all, and any reviewer who nevertheless signs off is doing it from
memory — which is the thing this convention exists to abolish.

This file is a repository document.

## The footer

Every review artefact ends with this block, adapted only to name the
specific artefacts in play and to say where their digests are
published:

    Please end your reply with these six items:
      Reviewer: your name and role if you are a person; model name and
                version as precisely as you can state it, and the
                interface you are running in, if you are a model
      Assessed: the exact filename or subject you were given
      Assessed source dated: its internal date and time, or "not stated"
      Repository: repo, branch and PR as stated in the artefact you were
                given, or "not stated"
      Reply ended: a real clock reading taken now, with timezone
      Verification: VERIFIED MATCH, VERIFIED MISMATCH or UNABLE TO
                VERIFY, for EACH artefact you were sent, named
                separately, with the digest you computed. The artefact
                carrying this footer is verified against the
                BODY-SHA256 in its own header, over every byte after
                its marker line. Any repository document attached to it
                is verified whole-file, against the digest published in
                the covering artefact
    If you cannot state your exact model identifier, or have no clock
    access, write that plainly in the item concerned rather than
    omitting it, estimating, or guessing a version number.

## Why the escape clauses matter more than the items

A reviewer with no clock, asked for a real clock reading and given no
permitted way to decline, will supply a plausible one. **An invented
timestamp is worse than a missing one**, because it is indistinguishable
from a real one and gets filed as evidence. The same holds for a model
version: a guessed version number is worse than "exact identifier not
exposed", which is an accurate statement about a real limitation. Every
item here is more useful answered honestly than answered completely. A
reply saying "no clock access" is a good reply.

## Verification

The `Verification:` item refers to a header carried by review artefacts:

    BODY-SHA256: <digest of every byte after the marker line>
    BODY-BYTES: <count of those bytes>
    --- BODY BELOW THIS LINE ---

A file cannot state the digest of the whole of itself, but it can state
the digest of everything below a marker. That makes the check
self-contained: no covering message, no separate manifest, and nothing
to fetch.

**Which marker, and when there is none.** In a **review artefact** the
marker is the first occurrence of that line, standing at the top
immediately after the two header lines; everything after it is the body.
A **repository document** has no header and therefore no marker at all:
any occurrence of that string in it is ordinary content — as in this
section — and the whole file is hashed. A reviewer who finds the string
in the middle of a file has found text, not a header.

Three outcomes, and the third is a real answer rather than a failure:

- **VERIFIED MATCH** — the digest was computed over the bytes assessed
  and agrees with the header.
- **VERIFIED MISMATCH** — it was computed and differs. Report both
  digests.
- **UNABLE TO VERIFY** — no hashing mechanism, or no access to the raw
  bytes. A copy that cannot be hashed is still usable for review; its
  byte integrity is simply unestablished, and saying so is accurate.

Reviewers that do hash should report the digest they computed, so that a
round produces evidence of checking rather than an assertion of it.

### What to do about a mismatch

A mismatch is not on its own a licence to ignore the affected parts.
Some transfer routes damage a document predictably: on the evidence of
this project, pasting into a chat interface has stripped every blank
line on every occasion it has been checked, while attaching a file has
preserved them exactly. Both observations come from a subset of the
participants rather than from all of them.

Where a specific difference has been **established** against the
canonical copy, say so once at the top of the reply, proceed, and raise
nothing that depends on the missing bytes. Where it has not, report
integrity as **unresolved** and name the checks that could not be
completed. A mismatch alone does not establish that the known damage is
the *whole* difference, and treating it as though it does produces a
false clearance as readily as a false defect report.

### What `UNABLE TO VERIFY` means, and when it is itself a finding

The string covers three different situations: a reviewer with no
hashing mechanism, one that has it and did not use it, and one
answering plausibly without checking anything.

So it is falsifiable only against a record of who can hash. Once a
capability probe has established that for a given reviewer, **`UNABLE
TO VERIFY` from a reviewer known to be capable is itself a finding**,
not an accepted outcome. Without that record it remains an unfalsifiable
answer, which is why the capability record and this convention are used
together.

## What the header does not prove

**Integrity, not authenticity.** The header proves the body survived
transfer intact and is internally consistent. It proves nothing about
provenance: alter the body, recompute the header, and every reviewer
reports a match. **Authenticity comes from the commit-pinned URL.** The
two mechanisms are complementary and neither substitutes for the other.

**Transport, not capability.** The header removes the dependency on a
covering message reaching the reviewer. It does not remove the need for
the reviewer to be able to hash. One that cannot is exactly where it
was.

## Byte discipline

A hash discipline generates noise without a byte discipline. Every
document in this repository, and every review artefact sent from it:

- uses LF line endings, never CRLF;
- ends with exactly one newline;
- has its digest taken over the raw bytes, with `sha256sum` or
  equivalent.

One documented exception exists. `recurring-block-patterns.md` predates
this discipline and ends without a trailing newline. It is not
normalised in place, because its current digest has already been
published to reviewers and changing it silently would be
indistinguishable from tampering. It is normalised at the point it moves
to `registers/`, in a single commit, with both digests recorded there
and a notice circulated to reviewers beforehand.

For a review artefact the header is regenerated whenever the body
changes. That is one command and should be scripted rather than
remembered — the same principle as the rest of this file.

## A note on where requirements live

The reason this convention is written down at all is that an earlier
version of it asked the operator to append the footer to every message
by hand. That is a mechanical need placed in a human's path, and it was
correctly refused.

The general rule it produced is worth stating on its own: **if
something must accompany every message to a reviewer, it belongs inside
the artefact, not in a habit.** A person who has to remember it will
eventually be tired, and the failure is silent.

Where a platform offers persistent instructions scoped to a project, a
custom agent or a saved context, that is a reasonable second layer.
Account-wide instructions are a poorer fit, since they would attach this
to unrelated conversations. Nothing here depends on that layer existing.
