# Digest register

Files whose bytes have changed since a digest was published to
reviewers. One entry per change, with both digests and the commit that
separates them.

## recurring-block-patterns.md → registers/recurring-block-patterns.md

Changed 10 September 2026. One `0x0a` appended to the end of the file;
no other byte altered. The file moved from the repository root to
`registers/` in the same commit.

Before, at commit 5383614fd14fb0eca1dcfc38aabcc1bfe9489006:
  path    recurring-block-patterns.md
  bytes   1290
  sha256  895b332432e88c62ea6556de7312decdb7599f83dfd100dcc3fa47724d90074d
  blob    cb985085b9ac0e17407fb33147799775869138ff

After, at the commit that adds this entry:
  path    registers/recurring-block-patterns.md
  bytes   1291
  sha256  f156301cdcfa3902f60aaa8885664ab9378a49ab3f6f405298377173dc82394d
  blob    b9e97e54894bcc298cc47bae1d8449a36317239c

A notice was circulated to the reviewers holding the earlier digest on
10 September 2026, before the change was made, as
`conventions/reviewer-sign-off.md` requires; one of them independently
recomputed the successor digest from the published bytes and confirmed
it beforehand. **Both facts are recorded here by the orchestrating
window from its own record. The notice and the replies are not
committed to this repository, so a reader of the repository alone
cannot check them** — they are stated, not evidenced.

The earlier digest remains correct for the commit it was taken from. It
is superseded, not wrong.
