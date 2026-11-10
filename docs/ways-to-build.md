# Ways to build an app with AI

These are **forms of building**, not brand names. A project can mix more than one. Pick the form first; then optionally add a process pack such as ECC.

## 1. Autocomplete

You type. The AI suggests the next few lines.

**Tools:** GitHub Copilot, Cursor Tab, similar inline completions.

**Use when:** you already know the code you want, and you need speed on boilerplate.  
**Do not use as:** the only method for a whole product.

## 2. Chat in the editor

You describe a change. The AI reads the project and edits specific files. You review the diff.

**Tools:** Cursor Chat / Composer, VS Code Copilot Chat.

**Use when:** “add a filter to this page”, “explain this function”, “fix this bug”.  
**Weak when:** creating a whole product from zero in one prompt.

## 3. Coding agent

You set a goal. The AI explores the repo, writes files, runs commands, and iterates. You own the Git repository.

**Tools:** Cursor Agent, Claude Code, Codex CLI, OpenCode, Cline.

**Use when:** a real app that will grow (accounts, database, domain rules).  
**Needs:** someone who can read the code, run it, and reject bad changes.

This is the form that process packs (ECC, Superpowers, Spec Kit) sit on top of.

## 4. Prompt-to-app (“vibe coding”)

You describe the app in a browser. The tool generates a UI (often auth and a database too), shows a live preview, and can publish.

**Tools:**

| Tool | Typical output |
| --- | --- |
| Lovable | Web app + login + database (often Supabase) |
| Bolt | Full-stack prototype in the browser |
| v0 (Vercel) | Polished React/Tailwind screens to paste into a project |
| Replit Agent | App that runs in Replit’s cloud |

**Use when:** a demo this week, a landing page, “show the idea”.  
**Weak when:** you must keep the code for months, or when rules are strict (payments, disputes, legal invoices). After many prompts the app often becomes inconsistent, and you depend on that vendor.

## 5. Spec-driven

You write **what the software must do** (and how to check it) before anyone generates code. Then the AI implements one slice.

Typical files: `requirements.md` → `design.md` → `tasks.md` → implement.

**Tools:** GitHub Spec Kit, OpenSpec, AWS Kiro, or three Markdown files plus Cursor Plan mode.

**Use when:** money, permissions, auctions, status machines, anything that must not drift.  
**Cost:** slower to start; fewer invented features.

## 6. Process packs

These do **not** generate the app. They tell the coding agent how to behave: plan, write tests, review.

**Tools:** ECC, Superpowers, BMAD, GSD. See [similar-tools.md](similar-tools.md).

You still need form 3 (or sometimes form 4). A process pack on top of Lovable is almost useless. A process pack on top of Cursor or Claude Code is useful.

## 7. Cloud / background agents

You describe a task. A remote agent clones the repo, implements it, and opens a pull request. You review like a teammate’s work.

**Tools:** Cursor Cloud Agents, some Claude Code / Codex remote runs.

**Use when:** the spec for a slice is already approved.  
**Still needs:** a human merge and a real check of the feature.

## Usual pipelines

Fast demo:

```text
Idea → Lovable / Bolt / v0 → publish → stop (or export and rewrite)
```

Product you own:

```text
Idea
  → (optional) v0 / Lovable for a visual sketch
  → short spec in the repo
  → coding agent (Cursor / Claude Code)
  → (optional) ECC or Superpowers as the work loop
  → Git + review + deploy
```

## What Cursor already covers

If you work in Cursor, you already have: Plan mode, Agent mode, rules, skills, subagents, Bugbot-style PR review, a browser for checking the UI, and image generation. A process pack adds discipline (especially tests and security), not a missing editor.
