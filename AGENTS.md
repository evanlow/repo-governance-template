# AI Agent Guidance

This repository follows `prime_directive.md` and the mandatory `PR_REVIEW_CLOSURE_POLICY.md` supplement.

- Agents must read `prime_directive.md` and `PR_REVIEW_CLOSURE_POLICY.md` before implementation.
- Agents should make small, testable changes.
- Agents must avoid blind terminal commands.
- Agents must not assume paths, services, environment variables, database schema, or framework conventions without checking.
- Agents must preserve existing working behavior.
- Agents must not commit secrets.
- Agents must document test results and unresolved risks before handoff.

## Pull request review handling

When working on or assessing a pull request, agents must:

1. Read every issue comment, submitted review and inline review thread.
2. Treat human, Copilot, Codex and other automated-review feedback as requiring the same explicit disposition.
3. Reply to every review comment before recommending or requesting merge.
4. Record one of these dispositions in the thread:
   - `Fixed in <commit>` with a brief explanation and test evidence;
   - `No change` with the technical rationale;
   - `Deferred to #<issue>` with reason, owner and priority;
   - `Superseded by <commit or PR>` with an explanation;
   - a focused clarification request when the concern is unclear.
5. Re-run relevant tests after addressing feedback.
6. Request re-review for P0/P1, security, privacy, migration, data-integrity or production-reliability findings.
7. Not merge, recommend merge or mark a pull request ready while:
   - any review comment has no meaningful reply;
   - any current P0/P1 thread remains unresolved;
   - any blocking concern lacks a fix and re-review or explicit technical-owner risk acceptance;
   - required checks have not passed on the final head commit.
8. Update `session_log.md` with comments reviewed, fixes made, deferred concerns, tests run and remaining risks.

Thread status alone is not sufficient evidence: `outdated` does not prove a fix, and `resolved` must be supported by a recorded disposition.
