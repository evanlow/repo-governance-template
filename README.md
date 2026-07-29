# Project Name

Short description of the project.

## AI-Assisted Development

This repository uses `prime_directive.md` as the main engineering guideline for human contributors and AI coding agents.

Important supporting files:

| File | Purpose |
|---|---|
| `prime_directive.md` | Core engineering guidelines and principles |
| `PR_REVIEW_CLOSURE_POLICY.md` | Mandatory review-disposition rules and merge gate |
| `AGENTS.md` | General AI agent instructions |
| `.github/copilot-instructions.md` | GitHub Copilot repository instructions |
| `.github/pull_request_template.md` | PR and review-closure checklist |
| `.github/CODEOWNERS` | Automatic reviewer assignment (fill in before use) |
| `docs/BRANCH_PROTECTION.md` | Repository settings that enforce the policies |
| `session_log.md` | AI-assisted development session log |
| `.env.example` | Placeholder environment variables (never commit real secrets) |

## Development Rules

Before making changes:

1. Read `prime_directive.md` and `PR_REVIEW_CLOSURE_POLICY.md`.
2. Work on a feature branch.
3. Verify the environment.
4. Run relevant tests.
5. Do not commit secrets.
6. Document test results and risks before handoff.

Before merging:

1. Give every review comment a written disposition (`PR_REVIEW_CLOSURE_POLICY.md`).
2. Resolve every review thread; unresolved threads block the merge.
3. Confirm required checks pass on the final head commit.
4. Record the outcome in `session_log.md`.

## Starting a New Project From This Template

1. Replace the project name and description above.
2. Populate `.github/CODEOWNERS` with real owners.
3. Configure branch protection using the checklist in `docs/BRANCH_PROTECTION.md`, and verify it
   with a throwaway PR.
4. Replace the placeholder keys in `.env.example` with the ones your project actually needs.
5. Adapt the project-specific test commands referenced in `prime_directive.md`.
6. Extend the blocking-concern list in `PR_REVIEW_CLOSURE_POLICY.md` with your project's
   business-critical failure modes, and name the technical owner who may risk-accept them.
7. Add the first `session_log.md` entry before implementation begins.
