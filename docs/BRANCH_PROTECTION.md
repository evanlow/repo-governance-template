# Branch Protection & Enforcement Settings

`prime_directive.md` Principle 13 and `PR_REVIEW_CLOSURE_POLICY.md` describe how changes must be
reviewed. Documentation alone cannot block a merge — the settings below are what turn those
policies into enforced gates. Configure them once when starting a project from this template.

Settings live under **Settings → Branches → Branch protection rules** (or **Settings → Rules →
Rulesets** on newer repositories).

## Required settings for `main`

| Setting | Value | Enforces |
|---|---|---|
| Require a pull request before merging | On | Principle 13 — never commit to `main` |
| Require approvals | 1 or more | Principle 13 review requirement |
| Dismiss stale pull request approvals when new commits are pushed | On | Approval must apply to the final head commit |
| Require conversation resolution before merging | On | `PR_REVIEW_CLOSURE_POLICY.md` — no unresolved threads |
| Require status checks to pass before merging | On | Checks pass on the final head commit |
| Require branches to be up to date before merging | On | Checks run against the real merge result |
| Require linear history | Optional | Readable history; pairs with squash merge |
| Do not allow bypassing the above settings | On | Prevents silent policy bypass by admins |
| Allow force pushes | Off | Principle 13 — never force-push shared branches |
| Allow deletions | Off | Protects `main` |

Every row above is required except where marked Optional. If you configure only one of them, make it
**Require conversation resolution before merging** — it is what enforces
`PR_REVIEW_CLOSURE_POLICY.md`. Without it, the policy relies entirely on discipline.

## Repository-level settings

- **Settings → General → Pull Requests:** enable *Automatically delete head branches* (Principle 13
  — delete merged branches).
- **Settings → Code security:** enable secret scanning, push protection and Dependabot alerts
  (Principle 12 — never commit secrets).
- **`.github/CODEOWNERS`:** replace the `@OWNER-PLACEHOLDER` entry with real owners so reviewers are
  requested automatically. GitHub **silently ignores** rules that name a user or team without write
  access, so a leftover placeholder produces no error and no reviewer request — the file looks
  configured while doing nothing. Confirm the fix under **Settings → Code owners**, which lists any
  syntax or access errors, or by opening a PR and checking that the expected reviewer is requested.

## Solo projects

Requiring one approval on a solo repository blocks your own PRs, since GitHub does not let you
approve your own work. Options, in order of preference:

1. Set required approvals to **0** but keep **require conversation resolution** and **require status
   checks** on. Automated reviewers still produce threads that must be dispositioned, so the gate
   remains meaningful.
2. Add a second maintainer or a bot account as reviewer.
3. Keep approvals required and merge via an admin bypass — least preferred, because it defeats the
   purpose of the rule.

Whichever option you choose, the written-disposition requirement in
`PR_REVIEW_CLOSURE_POLICY.md` still applies.

## Verifying enforcement

Do not assume the configuration works. Prove it once:

1. Open a throwaway PR with a trivial change.
2. Leave a review comment and do not resolve it.
3. Confirm the merge button is blocked, citing the unresolved conversation.
4. Resolve the thread with a written disposition and confirm merge unblocks.
5. Record the result in `session_log.md`, then close the throwaway PR.

## Setup checklist

- [ ] Branch protection or ruleset created for `main`
- [ ] Require pull request before merging
- [ ] Require conversation resolution before merging
- [ ] Require status checks to pass, and branch up to date
- [ ] Dismiss stale approvals on new commits
- [ ] Force pushes and deletions disabled on `main`
- [ ] Bypass disallowed (or bypass actors explicitly documented)
- [ ] `.github/CODEOWNERS` populated with real owners, and no `@OWNER-PLACEHOLDER` entry remains
- [ ] CODEOWNERS verified to resolve (no errors under Settings → Code owners; reviewer auto-requested on a test PR)
- [ ] Secret scanning and push protection enabled
- [ ] Automatic head-branch deletion enabled
- [ ] Enforcement verified with a throwaway PR and recorded in `session_log.md`
