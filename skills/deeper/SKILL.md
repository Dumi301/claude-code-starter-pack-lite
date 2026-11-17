---
name: deeper
description: Rewrite a task or prompt into a deeper version of itself, not a bigger one, using Felix Rieseberg's four expert questions. Use when the user types /deeper followed by a task, or says "deeper not bigger", "make this prompt deeper", "what would a top expert do here", "raise the bar on this task". Not for small edits, simple questions, or adding scope.
---

# Deeper, not bigger

Source: Felix Rieseberg (works on Claude at Anthropic), "How to be more ambitious: A tutorial for humans with models", 13 October 2026, section Depth.
https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/

His prompt, verbatim:

> I want a deeper version of this task, not a bigger one. Before rewriting it: (1) say what a top professional in this field would do here that I'm not asking for; (2) name the rawest material they would start from instead of what has already been digested for me; (3) name the specific methods and tools they would use; (4) say what, other than you or me, would show the result is right. Then rewrite my prompt to ask for exactly that.

## How to run it

The task is whatever follows `/deeper` (or the task the user just gave).

1. Answer the four questions in writing, one or two lines each. Name the actual thing, never the category ("the Twilio delivery log", not "the data").
   1. What a top professional in this field would do here that was not asked for.
   2. The rawest material they would start from: logs, source files, the original document, the measurement. Say where it lives if known.
   3. The specific methods and tools they would use, and why each fits.
   4. What, other than the user or the model, would show the result is right: a test, a command, a reproduction, a real number, a reviewer. Say what counts as pass and as fail.
2. Rewrite the prompt to ask for exactly that: start from the raw material, use the named methods, end on the outside check.
3. Show the four answers and the rewritten prompt. Do the work only if the user handed over a task to do, not just a prompt to improve.

## Rules

- Same goal, same scope. No extra deliverables, features or side quests.
- No generic answers ("use best practices", "be rigorous").
- The model does not grade its own work: question 4 must name an outside check.
- If the raw material or the tool is missing, say what is missing instead of pretending.
