RECURRING-PATTERNS CHECKLIST — v2, amended 13 September 2026

A checklist for reviewers to check new drafts/findings against, in
addition to their own independent read. Maintained here so brief
revisions don't need to carry this content inline. Twelve patterns:
nine originally summarized in brief v17, one addition (item 8) from
Block 34 v1's own history, and two added on 13 September 2026 from
blocks that modified a tracked file rather than adding one.

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

=== END OF RECURRING-PATTERNS CHECKLIST v2 ===
