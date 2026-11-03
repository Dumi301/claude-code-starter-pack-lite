# CLAUDE.md - <project name>

Read this file first, every session. Then read `handoffs/LATEST.md`.

## NEVER (laws - comply fully or report the failure)
- Never report "done" without the verifying tool call in this session (file written, test run, request made). Prose alone is not done.
- Never state counts, metrics or statuses from memory when a command or file can be read. Read first, then report.
- Never soften a failure with narrative. Report the number or the error, one line. Context only if asked.
- Never claim a fix works without re-running the case that failed.
- Never create a new script, agent or config file when an existing one covers the job. Propose and stop.
- Never write real secrets into the repo. Placeholders in `.env.example` only; real values live in `<secrets-path-outside-repo>`.
- Never touch `<protected-paths>` (list them: production configs, locked docs, vendored code).
- Never take a destructive or irreversible action (delete, force-push, drop, purchase, send) without `<owner>` naming it in this session.

## Evidence rule
Numbers only from commands run this session. A claim in a report must carry its source: the command, or the file and line. If it cannot be verified now, write UNVERIFIED. Never fill the gap from memory.

## Output style
- Terse. Verdicts at most 15 lines. Worker prompts at most 25 lines.
- Show modified blocks only; no full-file rewrites unless asked.
- No recaps of tool output the user can already see.
- Verify edits with a tool call; do not narrate them.

## Logging rule
After every meaningful step append one line to `logs/<YYYY-MM-DD>.md` (see `logs/README.md`). Append-only, never read back. Per verified phase add an entry to `HANDOFF.md`. At session end, and at least every `<N>` hours when unattended, write a full handoff.

## Phase gates
Work in phases. Each phase:
1. **Plan**: name the files touched and the executable gate (command plus expected output) before writing code.
2. **Build**: one commit per phase; the message names the gate.
3. **Verify**: run the gate. Paste the real output. Use the verifier agent for noisy checks (screenshots, long test logs).
4. **Fix cycles**: at most 2. After that, stop and surface the failure to `<owner>`.
5. **Handoff**: append to `HANDOFF.md`; update `handoffs/LATEST.md` at session end.

A phase without an executable gate is not a phase; split it until it has one.

## Delegation
Work directly by default. Delegate only when a worker's isolated context is cheaper than the output landing in yours:
- (a) mechanical build over about 60 tool calls with a clear spec;
- (b) two or more disjoint-file streams in parallel;
- (c) noisy verification (screenshots, test logs).

Limits: at most 3 workers plus 1 verifier at once. Every dispatch names its model. A worker prompt states goal, exact files, constraints and gate, in at most 25 lines.

## Stack and commands
- Build: `<build command>`
- Test: `<test command>`
- Run: `<run command>`
- Lint: `<lint command>`

## Project facts
<Three to ten lines: what the project is, where the entry points are, anything easy to get wrong.>
