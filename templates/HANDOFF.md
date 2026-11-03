# HANDOFF

Running log of verified work. One entry per verified phase, newest at the bottom. Append only. Each entry: what ran, the output that proves it, what is next, what is open. Full end-of-session handoffs live in `handoffs/`.

Entry format:

    ## <YYYY-MM-DD> - Phase <N> <done|blocked> <short title>
    - Gate: `<command>` -> <real output, one line>.
    - Changed: <files, comma-separated>.
    - Next: <the single next step>.
    - Open: <questions or risks, or "none">.

Example entry (delete before use):

## 2026-01-15 - Phase 1 done CSV export endpoint
- Gate: `npm test -- export` -> 14 passed, 0 failed.
- Changed: src/export.ts, test/export.test.ts.
- Next: phase 2, wire the button in the reports page.
- Open: max row limit undecided (assumed 50,000).
