# AGENTS.md

**Language convention:** Conversational replies in 中文. All code, identifiers, comments inside code, commit messages, and log strings in English.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks (typo fixes, one-liners), use judgment.

---

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before writing any code:
- State key assumptions explicitly. If an assumption is load-bearing and uncertain, ask before proceeding.
- If multiple reasonable interpretations exist, list them and ask — don't pick silently.
- If a simpler approach exists than what was asked, name it and push back.
- If the request is unclear, stop. Name what's confusing. One specific question beats five vague ones.

---

## 2. Ground Yourself in the Code

**Read before you write. Don't fabricate.**

- Before editing a file, read it. Read its imports. Read the functions you plan to call.
- No invented APIs, file paths, library functions, or config keys. If unsure something exists, check or say so explicitly.
- Match the existing style, naming, and patterns of the codebase — even if you'd write it differently from scratch.
- For non-trivial edits, search for callers and tests of the code you're touching before changing it.

---

## 3. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for scenarios that can't occur.
- No premature optimization.

If you wrote 200 lines and 50 would do, rewrite. Ask: "Would a senior engineer call this overcomplicated?" If yes, simplify before submitting.

---

## 4. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- If you notice unrelated issues or dead code, mention them — don't fix silently.

When your changes create orphans:
- Remove imports, variables, and functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: every changed line should trace directly to the request.

---

## 5. Goal-Driven Execution

**Define success criteria. Loop until verified. Know when to stop.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass."
- "Fix the bug" → "Write a test that reproduces it, then make it pass."
- "Refactor X" → "Ensure tests pass before and after; behavior unchanged."

For multi-step tasks, state a brief plan first:

```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

When stuck:
- After two failed attempts at the same approach, stop and reconsider — don't keep patching.
- Report what you tried, what failed, and your next proposed step. Then ask.

When done, report concisely: what changed, what was verified, what wasn't. No marketing language ("comprehensive", "robust", "production-ready"). Just the facts.

---
