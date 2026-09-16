RECURRING-PATTERNS CHECKLIST — v5, amended 15 September 2026

A checklist for reviewers to check new drafts/findings against, in
addition to their own independent read. Maintained here so brief
revisions don't need to carry this content inline: nine originally
summarized in brief v17, one addition (item 8) from Block 34 v1's own
history, two added on 13 September 2026 from blocks that modified a
tracked file rather than adding one, three added on 14 September 2026
from a seven-round execution-block campaign, and five added on 15
September 2026 from a document-drafting campaign rather than a block
campaign — the first five here that concern the drafting window's own
work rather than the blocks it issues.

1. Doctrine-pointer misattribution — a targeted-read instruction
   attaching a list to the wrong document.
2. Commissioning verification of text that was never drafted.
3. Changelog-vs-instruction divergence — a fact a later step needs,
   stated only in explanatory prose.
4. Unstated cross-task dependency.
5. Not carrying forward an already-established fix into a
   structurally similar new block.
6. A fix narrowing/restoring one thing while accidentally widening
   a gap a different, earlier fix had closed.
7. Execute-vs-assess-only left ambiguous by format alone rather
   than stated explicitly.
8. Abbreviating standing elements because a block "feels small."
9. A pointer — ID, line number, date, entry name, file — that is
   real but stale or aimed at the wrong thing.
10. A changelog that describes a fix the body text does not
    actually contain.
11. A guard copied from an add-only block into a modifying one —
    `test ! -e <path>` is an absence test, and on a file the block
    requires to be present it returns exit 1, the chain
    short-circuits, the confirmation never prints, and the block's
    own rule then says stop. It cannot complete regardless of
    anything else.
12. A modifying block holding one digest where it needs two. The
    same file has a before value and an after value; a blanket
    substitution puts the after value in the before slot, and the
    block stops at its first check on a correct repository. Pin
    both, say which is which, and pin the insertion and deletion
    counts from `git diff --numstat` — one block stated a correct
    total with a wrong split, which stops an executor matching it
    exactly.
13. A fence that assumes state survives between calls without
    having probed whether it does. In the harnesses this project
    has measured, no shell variable, working directory, PATH entry
    or environment value persists from one tool invocation to the
    next — so a block splitting a check across two fences has
    already lost whatever the first established. **That is a
    measured property of those harnesses, not a rule about agent
    tool calls in general**: see `methods/recurrent-practices.md`
    section 6. Probe it, then either write every cross-call value
    to a file in a named state directory or keep the whole check
    in one fence.
14. A guard written as prose rather than as code. A sentence
    containing "confirm", "must match", "check that" or "STOP if"
    has no exit status, is followed inconsistently by careful
    executors, and cannot fail. Every guard is a command whose exit
    code decides, or it is not a guard.
15. Source quoted from memory rather than read. A block citing a
    file, a function signature, a line of configuration or a prior
    version must quote what is there now, fetched or read in this
    pass. Paraphrase from recollection is how a claim that was true
    once survives into a version where it is false — most often for
    something already got wrong once and corrected.

16. A recommendation to remove or rewrite committed text, made from a
    finding's summary rather than from the text. A finding describes
    what it found; the text is what will change. Read the bytes in the
    same pass and quote them. Where they cannot be quoted, the change
    cannot be recommended — a removal proposed from a summary once
    would have deleted accurate, working text to close a finding that
    needed no action.
17. A claim that a fix is in, written before it was applied. A
    commission stated that a guard had been narrowed while the original
    guard was still in the file. Every claim about the state of an
    artefact is checked against the artefact in the turn that makes it,
    not against the intention to make it.
18. Working from whichever report is in front of you rather than from a
    ledger of all of them. Across one round, twenty of forty-six
    findings went unactioned — not refused, not recorded, simply not
    reached. Keep every finding from every reviewer in one list with
    one of three states: fixed and how it was tested, open and why, or
    ruled not a defect and on what evidence. Nothing leaves the list by
    being fixed; it changes state.
19. A batch of edits that writes its file once at the end. An assertion
    failing midway discards every edit before it, and the log still
    reports them as applied. Write after each edit, or verify the file
    afterwards rather than trusting the run.
20. A verification string that spans a line break. A check for a phrase
    that the file wraps across two lines reports absent for text that
    is present, and the next action is taken on a false negative.
    Search whitespace-insensitively, or against a single line.

=== END OF RECURRING-PATTERNS CHECKLIST v5 ===
