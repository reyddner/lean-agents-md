# lean-agents-md

An instruction file that makes AI coding agents (Codex, Claude Code and others) **stop burning tokens for nothing**. Drop it in, and the agent reads it at the start of every conversation.

*Versão em português: [README.pt-BR.md](README.pt-BR.md)*

## Why agents burn so many tokens

On every step (each tool call) the agent re-reads the **entire** conversation so far. The bill grows with what piles up in the context, not with what the agent writes.

A real session that ran out of tokens in under an hour:

| | Tokens |
|---|---|
| Read (input), across ~50 steps | **5.3 million** |
| Written (output) | 39 thousand |
| Context re-read per step at the end | ~90 thousand |

What filled the context: dozens of page renders opened "to double-check", large command outputs printed in full, and a whole new pipeline written instead of changing parameters in the existing one. The same project, done in short steps, barely used any tokens.

## What the file tells the agent

- Open only the images that matter (3–4 per reply, low resolution); check with code when possible.
- Never print large files in full; use `head`, `grep`, counts.
- Read only the code it will change.
- Reuse existing scripts instead of rewriting or copying the project.
- On reviews, list findings first and fix only what you choose.
- Short steps; warn before big tasks.
- Keep a `HANDOFF.md` so the next conversation picks up where this one stopped.

## Install

| Agent | All projects | One project |
|---|---|---|
| Codex | `~/.codex/AGENTS.md` | `AGENTS.md` at the project root |
| Claude Code | `~/.claude/CLAUDE.md` | `CLAUDE.md` at the project root |

`CLAUDE.md` in this repo is the same content under the name Claude Code looks for. On Windows, `~` is `C:\Users\<you>`.

Portuguese versions: [AGENTS.pt-BR.md](AGENTS.pt-BR.md) (rename to `AGENTS.md` or `CLAUDE.md` when installing).

If you already have one of these files, paste the sections in instead of replacing it.

## Tips beyond the file

- **Start a new conversation per stage** (review in one, fix in another). The context resets, and that is the biggest saving.
- Say it in the request when it matters: "don't open images", "use the existing scripts".

## License

[CC0 1.0](LICENSE): public domain. Copy, change and share freely, no attribution needed.
