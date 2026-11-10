# Working loop (any project)

Use this whether or not ECC is installed. It is the same loop ECC describes, written so a person can follow it in Cursor or Claude Code.

```text
plan → test → implement → review → verify → remember → improve
```

Do **one thin slice** at a time. A slice is something you can show: a catalog page, a publish form, a status change. Not “the whole backend.”

## Roles

You stay the operator: you set the goal and try the result.

| Role | Job |
| --- | --- |
| Planner | Restate the slice, risks, steps, success checks. **Stop until you say yes.** |
| Builder | Implement only what the plan listed |
| Reviewer | Read the diff in a new chat / fresh context |
| Fixer | Only the review findings, then stop |

In Cursor: Plan mode (or a planning prompt) → Agent mode to build → new Agent chat to review. Do not plan and implement in the same turn if the slice is risky.

## Plan (before files exist)

The assistant should:

1. Restate the request in one paragraph.
2. List what is in scope and what is not.
3. List risks (data loss, wrong money math, duplicated installs, secrets).
4. Ordered steps with dependencies.
5. How you will know it worked (visible checks, not “looks good”).
6. Wait for **yes / proceed**. A prompt that contains an example is not approval.

If you change the plan, run this step again. Do not start coding from a stale plan.

## Tests

- **No domain rules yet** (static page): written checks are enough (“home renders in the product language”, “no login form”).
- **Rules exist** (prices, status transitions, who may rate): write the failing check first, then the code. RED → GREEN → refactor.
- A paragraph that says “we will test X” is not a test. A test is something that can fail.

Keep money in integer minor units (cents). The server decides status and winners, not the phone clock.

## Implement

- Only the files the plan named.
- One stack. Do not add a database “for later” on a slice that does not save data, unless you already decided the app is real and the database is the source of truth from day one. Be consistent: either prototype in the browser, or own a server from slice 1. Do not mix halfway without a written decision.
- Product copy in the language you chose. Do not silently switch.

## Review

New context. The reviewer gets the diff and the plan, not the builder’s excuses.

Look for: extra scope, secrets in the repo, status changes from the client, missing empty/error states, tests that assert nothing.

## Verify

You click through the slice the way a user would. A screenshot of the happy path is not verification. Check empty lists, failed validation, and (if relevant) a second user who must not see the first user’s data.

## Remember

After a slice that taught something durable, write **one short rule** in the project (README or `.cursor/rules`):

- language and tone
- commission / tax / rounding
- “server is the authority”
- demo vs real payments
- which install path you use for AI tools

Do not save giant transcripts. Save the decision.

## Improve

If the same mistake appears twice, add a test or a rule. Do not add a new framework.

## Security, when it matters

Before real sign-up or real money:

- Review auth, uploads, secrets, and who can change order or bid state.
- Optional: AgentShield (`ecc-agentshield`) on the agent config and the repo.
- Optional: Cursor security-review / Bugbot on the pull request.

Scans are aids. They do not replace reading the payment and data rules.

## Human gate

Nothing in this folder is permission to generate application code in another repository. Approval is a message in the session where the work will happen, for that slice only.
