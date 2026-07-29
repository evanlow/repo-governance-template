# Pull Request Review Closure Policy

This policy supplements `prime_directive.md` and applies to all human contributors, AI coding agents, automated reviewers and maintainers working in this repository.

## Policy objective

Every review comment or concern deserves an explicit response before merge. Silence is not an acceptable disposition because it leaves no reliable record of whether the concern was fixed, rejected, deferred or overlooked.

## Required disposition for every review concern

Before merge, every issue comment, review submission and inline review thread must have a recorded disposition from the pull request author or responsible implementer.

Use one of the following dispositions:

### 1. Fixed

- Explain what changed.
- Identify the corrective commit or the relevant updated code.
- State the tests or verification performed where appropriate.

Example:

> Fixed in `abc1234`. The redirect now accepts only safe relative paths, and a regression test covers absolute external URLs.

### 2. Accepted without change

- Explain why the current implementation is correct or why the concern does not apply.
- For material disagreements, obtain reviewer or designated technical-owner acknowledgement before merge.

### 3. Deferred

- Explain why the concern is outside the current scope or release.
- Create and link a follow-up GitHub issue.
- Record an owner, priority and acceptance criteria in that issue.
- A blocking concern cannot be deferred merely to meet a target date unless the designated technical owner explicitly accepts the risk.

### 4. Superseded

- Identify the later commit, pull request or design change that made the concern obsolete.
- Briefly explain why the original concern no longer applies.

### 5. Clarification requested

- Ask a focused question and wait for clarification.
- Do not merge while a material concern is still awaiting clarification.

## Blocking concerns

A pull request must not merge with a current unresolved P0 or P1 concern.

The following concerns are blocking unless fixed and re-reviewed, or explicitly accepted by the designated technical owner with a documented rationale:

- security or secret exposure;
- authentication or authorisation;
- privacy or personal-data handling;
- data loss or transactional integrity;
- database migration or rollback safety;
- production reliability or availability;
- incompatible API or schema changes;
- correctness of any business rule the product is trusted to enforce;
- any issue that can cause duplicate, missing or corrupted records.

> **Adopting this template:** extend the list above with the failure modes that are
> business-critical for your project, and name the designated technical owner who is
> allowed to risk-accept a blocking finding.

A reply alone is not sufficient for a blocking finding. The record should normally include:

1. a corrective change;
2. an appropriate test or verification;
3. a reply identifying the fix;
4. reviewer acknowledgement, re-review or thread resolution.

## Thread status and evidence

GitHub thread status is supporting evidence, not the whole control:

- `Resolved` does not prove that the issue was fixed unless the thread records its disposition.
- `Outdated` means the relevant diff changed; it does not automatically prove the underlying concern was corrected.
- A current unresolved thread must be treated as open unless the discussion clearly records an approved disposition.

## Final merge gate

Before merging, the person performing the merge must confirm that:

- every review comment has received a meaningful response;
- every current review thread has a recorded disposition;
- all blocking findings are fixed and re-reviewed or formally risk-accepted;
- deferred findings have linked issues with owner, priority and acceptance criteria;
- required automated checks pass against the final pull request head commit;
- relevant documentation and tests have been updated;
- `session_log.md` records the final validation, unresolved risks and handoff status.

## Minimum response templates

### Fixed

> Fixed in `<commit>`. `<brief explanation>`. Validation: `<tests or evidence>`.

### No change required

> No change proposed. `<technical explanation>`. `<reviewer or technical-owner acknowledgement, when material>`.

### Deferred

> Deferred to `#<issue>` because `<reason>`. Owner: `<owner>`. Priority: `<priority>`. This does not block the current merge because `<risk rationale>`.

### Superseded

> Superseded by `<commit or PR>`. `<explanation of why the concern no longer applies>`.

## Responsibility

- The pull request author or implementer is responsible for replying to every comment.
- The reviewer is responsible for confirming whether blocking feedback has been satisfactorily addressed.
- The merger is responsible for enforcing the final merge gate.
- AI agents must not recommend merge while any review comment lacks a response or any blocking concern remains open.

## Solo projects

The policy still applies when there is no second reviewer. Perform an explicit self-review
pass against the checklists in `prime_directive.md` Principle 13, record a written
disposition for each automated-reviewer finding, and treat your own unresolved concerns as
blocking. The record, not the approval, is the control.

## Enforcing this policy

Written policy alone does not block a merge. See `docs/BRANCH_PROTECTION.md` for the
repository settings that turn this document into an enforced gate.
