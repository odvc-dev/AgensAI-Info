# How to choose for a new project

Use this at kickoff. Write the answers in the project README. Do not install a toolkit until the form of building is chosen.

## 1. What are you shipping?

| If the outcome is… | Form of building | Process pack |
| --- | --- | --- |
| Landing page, mock, class demo this week | Prompt-to-app (Lovable, Bolt, v0) | None |
| UI you will paste into a real repo | v0 for screens, then a coding agent | Optional Superpowers |
| Real app: accounts, database, you keep the Git repo | Coding agent (Cursor or Claude Code) | Spec + thin ECC or Superpowers |
| Long project that loses context | Same coding agent | GSD or Spec Kit |
| Team that needs an audit trail | Coding agent | BMAD or Spec Kit |
| Money, auth, personal data | Coding agent + tests | ECC TDD + reviewer; security scan before users |

## 2. Where do you work?

| Environment | Note |
| --- | --- |
| **Cursor** | Plan, Agent, rules, and review are already there. ECC’s Cursor path is beta. Prefer Superpowers, Spec Kit, or ECC as a **written checklist** first. |
| **Claude Code** | Native home of ECC and Superpowers plugins. |
| **Codex** | Native plugin possible; hooks are not the same as Claude’s. |
| **Browser only (no editor)** | Lovable / Bolt / v0. Do not start with ECC. |

## 3. Machine constraints

- **No Node.js:** you cannot install ECC, Next.js, or most CLIs. Use a browser builder, or install Node 18+ / 22 LTS first.
- **Windows native:** ECC learning/memory features have had open defects. Git Bash or WSL is safer for shell-heavy packs.
- **Google Drive as the project folder:** fine for documents; poor as the Git working tree (sync fights the editor). Keep code in a normal folder, copy deliverables to Drive.

## 4. Decision tree

```text
Need a clickable demo in hours?
  yes → Lovable / Bolt / v0. Stop or export later.
  no  → Will you keep this repo for months?
          no  → Chat + autocomplete in Cursor is enough.
          yes → Coding agent in your Git repo.
                  Domain rules are strict (money, permissions, status)?
                    yes → Write a spec (Spec Kit or three Markdown files).
                          Add TDD + reviewer (ECC four files or Superpowers).
                    no  → Superpowers, or no pack.
                  Real users soon?
                    yes → Security review / AgentShield before launch.
                    no  → Review each slice; scan later.
```

## 5. Do not do these

- Install ECC **and** Superpowers **and** BMAD on the same harness. They overlap and duplicate hooks.
- Stack two ECC install methods on one harness (plugin + `install.sh --profile full`).
- Load every rule pack. Rules are always in context.
- Treat prompt-to-app output as production without moving it into a repo you control.
- Invent numbers, legal citations, or “the provider supports escrow” without checking the provider’s own docs.

## 6. Kickoff checklist (copy into a new repo)

- [ ] Outcome: demo / real app / both
- [ ] Editor or builder: Cursor / Claude Code / Lovable / other
- [ ] Spec location: README only / `docs/` / Spec Kit
- [ ] Process: none / four ECC files / Superpowers / other
- [ ] Node.js installed if the stack needs it
- [ ] One install method per tool
- [ ] Language of the product UI
- [ ] What is out of scope for v1 (real payments, native apps, …)
- [ ] Who says “yes” before a slice is coded
