# Everything Claude Code (ECC)

ECC is an open-source **operating layer** for coding agents: skills, specialized subagents, hooks, rules, memory, and a security scanner. It is not a model and not a coding agent. You install it on top of Claude Code, Codex, Cursor, or similar.

- Site: [ecc.tools](https://ecc.tools)
- Source: [github.com/affaan-m/ECC](https://github.com/affaan-m/ECC)
- License: MIT (toolkit). Paid GitHub App / Pro is separate (~$19 per active seat / month for private-repo hosted workflows).
- Author: Affaan Mustafa. Best on Claude Code; Cursor support is labeled beta.

Typical catalog size (late 2026): on the order of 70 agents, 300+ skills, ~100 legacy command shims. Treat that as a **menu**, not a recommendation to install everything.

Tagline of the project: plan → test → implement → review → verify → remember → improve.

## What you actually get

| Piece | Role |
| --- | --- |
| **Skills** | Reusable workflows loaded on demand (TDD, security review, research, …) in `skills/*/SKILL.md` |
| **Agents** | Scoped workers: planner, architect, code-reviewer, security-reviewer, tdd-guide, … |
| **Commands** | Slash-command shims; ECC is moving to skills-first |
| **Hooks** | Scripts on events (before/after tools, stop, compact). Run outside the model context |
| **Rules** | Always-loaded standards. Cost context every session — install selectively |
| **Instincts / learning** | Patterns from sessions, with confidence scores |
| **Memory vault** | Harness-neutral Markdown handoffs (`ecc memory …`) |
| **AgentShield** | Scanner for agent configs: secrets, permissions, hook injection, MCP risk (`ecc-agentshield`) |

Related product pieces on ecc.tools: Plan Canvas, Control Pane, GitHub App that turns repo history into guidance.

## When ECC helps

Use it (or a slice of it) when:

- The project will last many sessions and keep growing.
- There is **money, auth, or other people’s data**.
- You want a repeatable loop instead of a new prompt style every time.
- You will review diffs and run tests, not only accept generated files.

## When to skip it

Skip a full install when:

- The work is a small landing page, a one-file script, or a disposable demo.
- You have not installed Node.js 18+ (the installer needs it).
- You would install the whole catalog “just in case”. That burns context.
- You only need what Cursor already has (Plan mode, review, rules).

Independent reviews of ECC often say: steal a few workflows; do not dump the catalog into every session.

## Two ways to use it

### Option A — written checklist (start here)

Read four official files. Follow them in conversation. Install nothing.

Checked against `affaan-m/ECC` around 6–8 November 2026. Pin links to a commit when you copy this into a project.

| File | Habit |
| --- | --- |
| `commands/plan.md` | Restate the work, list risks, wait for an explicit human yes before code |
| `agents/planner.md` | Plan shape: steps, dependencies, risks, tests, success checklist |
| `skills/tdd-workflow/SKILL.md` | Failing tests before implementation on domain rules |
| `agents/code-reviewer.md` | Review a real diff from a fresh context |

That is the whole starter set. “Use the planner” means follow those instructions. It does not mean an ECC agent process is running.

The open-source toolkit is free (MIT). ECC Pro is the hosted GitHub App. Model/API bills are separate from both.

### Option B — small project install

After Node.js 18+ is on the machine:

```text
npx ecc-universal install --guided
```

Or, inside Claude Code only:

```text
/plugin marketplace add https://github.com/affaan-m/ECC
/plugin install ecc@ecc
```

Rules of thumb:

- **One install method per harness.** Plugin + full manual install duplicates hooks and skills.
- Preview with `--dry-run` when the CLI offers it.
- Install into **one project**, not the whole machine, until you know you want it globally.
- Add only `rules/common` plus **one** language pack you actually use.
- Hook profiles: `off | minimal | standard | strict`. Start at `standard` or `minimal`.
- Cursor is a beta adapter (files under `.cursor/`). Do not expect full Claude Code parity.

Verify with `/plugin list` (Claude) or the installer’s doctor command. If things appear twice, uninstall and pick one path. Do not stack.

## What to take vs skip

| Take | Skip at first |
| --- | --- |
| Planner, TDD skill, code reviewer | The other ~65 agents |
| `rules/common` + TypeScript (or your language) | All language packs at once |
| AgentShield before real users | Continuous learning / instincts on native Windows (known defects) |
| Security-reviewer on auth and payments | Memory vault until you actually switch harnesses |
| e2e skill when you have pages to open | Swarm / 100-agent setups |

## Suggested loop by kind of work

| Kind of slice | Loop |
| --- | --- |
| UI catalog, copy, layout | plan → build → review |
| Forms that save data | plan → test → build → review |
| Money, status machines, auctions, permissions | plan → **tests first** → build → review → **security review** |
| Before real users | AgentShield (or equivalent) on the repo |

## Install and security notes

- Guided setup needs Node.js 18+; Claude plugin setup also needs Git and Claude Code 2.1+ on `PATH`.
- Native Windows: core CLI works with limits; some learning/memory paths want Git Bash or WSL.
- Hooks execute shell commands. Treat `hooks.json`, MCP configs, and skills as executable configuration.
- AgentShield inspects prompts, hooks, MCP, permissions, and secrets. A scan is a review aid, not a guarantee.
- If a scan and a working exploit/PoC are both requested: keep the **fix and scan**; refuse exploit write-ups.

## Naming

Three public identifiers, not interchangeable:

- GitHub: `affaan-m/ECC`
- Claude plugin: `ecc@ecc`
- npm: `ecc-universal` (tracks release tags, not every commit on `main`)
