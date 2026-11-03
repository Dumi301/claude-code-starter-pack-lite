---
title: <project> handoff <YYYY-MM-DD> <slug>
type: handoff
created: <YYYY-MM-DD>
---
# Handoff - <slug>

Written for a fresh session that remembers nothing. Read top to bottom, then run the "Verify state" commands before trusting anything here.

## 1. State (3 lines max)
<What is built, what works, what does not.>

## 2. Verify state (run these first)
    <command 1>   # expect: <output>
    <command 2>   # expect: <output>

## 3. Done this session
- <phase>: gate `<command>` -> <real output>.

## 4. Next step (exactly one)
<The first action, specific enough to start without reading anything else.>

## 5. Open items and decisions
- Decided by <owner> on <date>: <decision>.
- Open: <question, who can answer>.

## 6. Traps and lessons
- <Something that cost time. How to avoid it.>

## 7. Where things are
- Secrets: <path outside repo>. Never in this file.
- Logs: `logs/<date>.md`.

---
# WORKED EXAMPLE (delete everything from this line down in real use)

```
---
title: shop-api handoff 2026-01-15 csv-export
type: handoff
created: 2026-01-15
---
# Handoff - csv-export

## 1. State
CSV export endpoint built and tested. UI button not started. Staging deploy untouched.

## 2. Verify state
    git log --oneline -3                            # expect: top commit "phase 1: export endpoint (gate: npm test -- export)"
    npm test -- export                              # expect: 14 passed, 0 failed
    curl -s "localhost:3000/export?limit=5" | wc -l # expect: 6 (header + 5 rows)

## 3. Done this session
- Phase 1: gate `npm test -- export` -> 14 passed, 0 failed.
- Phase 1b: streaming checked on a 40,000-row fixture: `curl ... | wc -l` -> 40001.

## 4. Next step
Phase 2: add an Export button to `src/pages/Reports.tsx` calling `/export` with the active filters.
Gate: Playwright test `export-button.spec.ts` (write it first).

## 5. Open items and decisions
- Decided by the owner on 2026-01-15: CSV only, no XLSX.
- Open: row cap. Assumed 50,000; owner to confirm before phase 3.

## 6. Traps and lessons
- The test DB seeds on first run only; if counts look wrong, delete `test.db` and re-run.
- Filters arrive as repeated query keys, not comma lists. The first parser assumed commas and passed its own tests.
  Lesson: test against real request shapes, not the shape you imagined.

## 7. Where things are
- Secrets: <secrets-path-outside-repo>.
- Logs: `logs/2026-01-15.md`.
```

And the matching LATEST.md line:

    Latest: `handoffs/2026-01-15-csv-export.md` (export endpoint done and tested; next: Export button, phase 2).
