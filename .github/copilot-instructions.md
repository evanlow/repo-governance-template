# Copilot Repository Instructions

Follow `prime_directive.md` and the mandatory `PR_REVIEW_CLOSURE_POLICY.md` supplement for all implementation and review work in this repository.

## Required Workflow

- Read and follow `prime_directive.md` and `PR_REVIEW_CLOSURE_POLICY.md` before making code changes.
- Work on a feature branch, not directly on `main`.
- Inspect existing code before editing.
- Verify the project environment before running commands.
- For Python projects, use the existing virtual environment if present; do not create a duplicate venv.
- Run relevant baseline tests before changes where practical.
- Add or update tests for backend logic changes.
- For UI changes, perform manual browser smoke testing and check browser console errors.
- Never commit secrets, `.env`, credentials, API keys, passwords, or tokens.
- Investigate anomalies instead of applying unexplained workarounds.

## Pull Request Review Closure

- Read every issue comment, submitted review and inline review thread on the PR.
- Treat human, Copilot, Codex and other automated-review feedback as equally requiring an explicit disposition.
- Reply to every review comment with one of: `Fixed in <commit>`, `No change` plus rationale, `Deferred to #<issue>` with owner and priority, `Superseded by <commit or PR>`, or a focused clarification request.
- Re-run relevant tests after addressing feedback, and request re-review for security, privacy, migration, data-integrity or production-reliability findings.
- Never recommend merge while any comment lacks a meaningful reply, any blocking concern is open, or required checks have not passed on the final head commit.
- Thread status is supporting evidence only: `outdated` does not prove a fix, and `resolved` must be backed by a recorded disposition.

## Required Handoff Report

Before handoff, always report:

- files changed
- tests run
- test results
- manual checks performed
- known risks or follow-up actions
