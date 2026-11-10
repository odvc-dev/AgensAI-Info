# Tools similar to ECC

Same job as ECC (give the agent a way of working), different bets. None of these replace picking a coding agent or a prompt-to-app tool.

## Direct bundles (agents + skills + workflow)

| Project | Difference from ECC |
| --- | --- |
| **[obra/superpowers](https://github.com/obra/superpowers)** | Small curated loop: brainstorm → worktree → plan → TDD → subagent build → review → ship. In Anthropic’s official plugin marketplace. Best default if ECC feels too large. |
| **[wshobson/agents](https://github.com/wshobson/agents)** | Modular marketplace: install only the plugin you need. Stronger Cursor / Codex / Copilot adapters than ECC. |
| **[SuperClaude Framework](https://github.com/SuperClaude-Org/SuperClaude_Framework)** | Command-and-persona toolkit (slash commands, modes, MCP). On-demand arsenal, not a mandated SDLC. Claude Code first. |
| **[garrytan/gstack](https://github.com/garrytan/gstack)** | “Virtual team” roles: product interrogation, review, QA in a real browser, security pass, ship. Opinionated, Markdown, MIT. |
| **[EveryInc/compound-engineering-plugin](https://github.com/EveryInc/compound-engineering-plugin)** | Brainstorm → plan → build → review → **write down what you learned**. Runs on many hosts including Cursor. |
| **[oh-my-claudecode](https://github.com/Yeachan-Heo/oh-my-claudecode)** | Claude coordinates parallel Claude / Gemini / Codex workers. For multi-model fan-out. |

## Process frameworks (they enforce an SDLC)

| Project | Bet |
| --- | --- |
| **[BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)** | Role pipeline (analyst → PM → architect → dev → QA) with durable decision documents. Clarify → Plan → Build/Verify → Learn. |
| **[GSD — Get Shit Done](https://github.com/gsd-build/get-shit-done)** | Fight context rot: small plans, each executed in a **fresh** context. State in files such as `PROJECT.md` / `STATE.md`. |
| **[claude-code-sdlc](https://github.com/Koroqe/claude-code-sdlc)** | Docs-first, TDD, pre-merge gates. Process is enforced, not optional. |

## Spec-driven (the spec is the artifact)

| Project | Bet |
| --- | --- |
| **[GitHub Spec Kit](https://github.com/github/spec-kit)** | `constitution → specify → plan → tasks → implement → converge`. Plain Markdown. Works with many agents, including Cursor. |
| **[OpenSpec](https://github.com/Fission-AI/OpenSpec)** | Delta specs for existing codebases: propose → apply → archive. |
| **[AWS Kiro](https://kiro.dev)** | IDE/CLI where requirements, design, and tasks are first-class. You switch tools, you do not only add a plugin. |
| **[Tessl](https://tessl.io)** | Specs linked to tests + a registry of skills an org can roll out. |
| **[Claude Task Master](https://github.com/eyaltoledano/claude-task-master)** | Parse a PRD into ordered tasks. Lighter planning layer. |

## One job, done well

| Need | Tool |
| --- | --- |
| Memory across sessions | [claude-mem](https://github.com/thedotmack/claude-mem), or `planning-with-files` (a live plan on disk) |
| Large agent fleets | [ruflo](https://github.com/ruvnet/ruflo) (formerly claude-flow). Heavy. Only if you truly run swarms. |

## Portable skills (build your own thin pack)

Anthropic’s **Agent Skills** format (`SKILL.md`) is the common unit. A skill can travel across Claude Code, Codex, Gemini CLI, and (via plugins) Cursor.

- Spec: [agentskills.io](https://agentskills.io)
- Official examples: [anthropics/skills](https://github.com/anthropics/skills)
- Install CLI / directory: [skills.sh](https://skills.sh) — `npx skills add anthropics/skills`
- Curated lists: [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills), [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)

Useful single skills: Anthropic **frontend-design** (UI that does not look generic), **skill-creator**.

## How they differ in one line

- **ECC:** large catalog + learned instincts.
- **Superpowers / GSD:** small opinionated process.
- **Spec Kit / BMAD:** documents as source of truth.
- **wshobson/agents:** à la carte plugins, better multi-harness install.

Most people mix: Superpowers or four ECC files for the loop, Spec Kit when a feature must stay specified, claude-mem only if sessions keep forgetting the project.
