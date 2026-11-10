# AgensAI Info

A personal guide for building software with AI. Use it at the start of any project. It is not a product plan and it is not tied to one app.

Last updated: 9 November 2026.

## Start here

1. Read [Ways to build with AI](docs/ways-to-build.md). Pick **where the code lives**.
2. Read [How to choose](docs/choose.md). Match the form to the size of the work.
3. If the project will grow, add a **process layer**: [ECC](docs/ecc.md) or a lighter alternative in [Similar tools](docs/similar-tools.md).
4. Follow the [working loop](docs/working-loop.md) on one thin slice at a time.

## The two layers

Do not mix these up.

| Layer | Question | Examples |
| --- | --- | --- |
| **Where the code is written** | Which tool produces the app? | Cursor, Claude Code, Lovable, Bolt, v0 |
| **How you control the AI** | What process does the AI follow? | ECC, Superpowers, spec-driven, “just prompt” |

ECC and Superpowers sit in the second layer. They do not generate the product. They tell a coding agent how to plan, test, and review. You still need a place where files are written (usually an editor agent in your Git repo).

## Official ECC sources only

If you use Everything Claude Code, install only from:

- Repository: [github.com/affaan-m/ECC](https://github.com/affaan-m/ECC) (the old name `everything-claude-code` redirects here)
- Site: [ecc.tools](https://ecc.tools)
- npm: `ecc-universal`, `ecc-agentshield`
- Claude plugin slug: `ecc@ecc`

Unofficial mirrors can ship hooks that run shell commands. Treat them as untrusted.

## Documents

| File | What it is for |
| --- | --- |
| [docs/ways-to-build.md](docs/ways-to-build.md) | Autocomplete, chat, coding agents, prompt-to-app, specs, process packs, cloud agents |
| [docs/ecc.md](docs/ecc.md) | What ECC is, when it helps, what to skip, small starter set |
| [docs/similar-tools.md](docs/similar-tools.md) | Superpowers, Spec Kit, BMAD, GSD, memory and swarm tools |
| [docs/choose.md](docs/choose.md) | Decision tree for a new project |
| [docs/working-loop.md](docs/working-loop.md) | Plan → test → build → review, without installing a toolkit |

## Rule of thumb

- Small demo or landing page: prompt-to-app (Lovable, Bolt, v0) is enough. Skip ECC.
- Real app you will keep: coding agent in your repo (Cursor or Claude Code) + a short spec + a thin process (four ECC files, or Superpowers).
- Money, auth, or other people’s data: tests first, then a security review before real users.
