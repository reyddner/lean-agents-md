# Instructions for the AI agent

## Token economy (applies to every conversation)

Every step re-reads the whole conversation context, so cost grows with everything that goes into it. Work lean:

- **Images**: don't open images, rendered PDFs or screenshots to "check everything". Check only what has a known problem or what I ask for, at most 3–4 per reply, at low resolution. Prefer checking with code (counts, text search, automated validation) over looking at the image.
- **Command output**: never print large files in full (JSON, logs, CSV, dumps, PDF text). Use `head`, `grep`, counts and summaries.
- **Reading code**: read only the parts you are going to change (search + line range), not whole files or the whole project.
- **Reuse, don't rewrite**: if the project already has a script, function or generator that does the job, change the data or parameters and run what exists. Don't copy the project into a new folder or build a parallel version unless I ask.
- **Reviews** ("review this", "check if it's right"): first give a short list of findings, changing nothing. Fix only after I choose what to fix.
- **Short steps**: make the change, run it once, check the minimum and deliver. Don't loop through generate → look at everything → adjust.
- **Warn first** when a task will need many images, many files or a lot of rewritten code, with a rough size estimate.

## How to work with me

- Be direct and brief.
- Ask before decisions that change the outcome and that only I can make; for the rest, pick the sensible default and tell me which one you picked.
- Check the code before stating something about it.
- When done, say in a few lines what changed and what is still pending.
- Never put passwords, tokens or keys in files or replies.

## Continuity between conversations (HANDOFF.md)

- At the start, if there is a `HANDOFF.md` at the project root, read it first and use it as the starting point.
- When you finish a task that changed files, or when I say I'm stopping, create or update `HANDOFF.md` (up to ~100 lines): **Goal**, **Current progress**, **What worked**, **What didn't work**, **Next steps**.
- Update the existing file instead of starting over; remove what is outdated.
