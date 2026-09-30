# DoNation Development Contribution Standard

## 1. Purpose

DoNation uses GitHub as a controlled software-delivery system, not merely as code storage. These standards establish traceability, code quality, security, and delivery expectations for all developers contributing to DoNation repositories.

## 2. Jira-First Traceability

Material development work must have an approved Jira issue before or at the start of implementation.

Use the Jira key throughout the development lifecycle:

- Branch name should include the Jira key.
- Pull request title or description must include the Jira key.
- Commit messages should include the Jira key when practical.
- The Jira issue must include or reference the related pull request before closure.

Examples:

- Branch: `DEV-1273-eslint-configuration`
- Commit: `DEV-1273 Implement supported ESLint configuration`
- PR: `DEV-1273 | Implement ESLint configuration and quality gate`

Historical commits must not be rewritten solely to add Jira keys.

## 3. Branching Rules

- Do not make material changes directly on a protected branch.
- Create a feature, fix, security, dependency, or infrastructure branch for material work.
- Keep a branch focused on one logical body of work.
- Pull or rebase from the appropriate base branch before final review when needed to reduce avoidable conflicts.
- Resolve merge conflicts deliberately. Do not blindly select one side without reviewing affected functionality.

## 4. Pull Request Rules

Every material change must be submitted through a pull request unless an explicitly approved emergency procedure applies.

A pull request must:

- reference the Jira issue;
- explain what changed and why;
- identify affected repositories, modules, or services;
- document testing performed;
- identify configuration, database, infrastructure, or deployment impact;
- document known limitations or deferred technical debt;
- include security/build/check results when applicable;
- avoid unrelated cleanup that obscures the intended change.

Do not combine unrelated changes into one pull request.

## 5. Commit Standards

Use meaningful commit messages that describe the actual change.

Preferred:

`DEV-1276 Constrain Twilio SDK dependency version`

Avoid:

- `fix`
- `changes`
- `update`
- `final`
- `working`
- `misc`

Commits should be understandable months later without requiring the developer who wrote them to explain what happened.

## 6. Code Must Be Pushed to GitHub

DoNation delivery code must not exist only on a developer workstation.

- Completed work must be pushed to an authorized DoNation repository.
- In-progress work that is part of an active delivery commitment should be pushed to an appropriately named branch or draft pull request at reasonable checkpoints.
- Code sent only through email, chat, ZIP files, or local storage is not considered delivered.
- Local-only work must not be represented as complete in Jira.

## 7. Secrets and Sensitive Information

Never commit passwords, API keys, AWS credentials, GitHub tokens, Twilio secrets, database credentials, private keys, authentication secrets, OTP values, sensitive `.env` contents, production-only credentials, or customer/member sensitive data.

Use approved secret-management mechanisms such as GitHub Environments/Secrets or AWS-managed secret services.

If a secret is accidentally committed, treat it as compromised and escalate immediately for rotation and remediation.

## 8. Dependency Management

- Do not use unbounded or wildcard dependency versions unless explicitly justified and approved.
- Avoid unnecessary mass upgrades while implementing an unrelated change.
- Commit lockfiles when required by the package manager.
- Review unexpected transitive upgrades or downgrades.
- Security findings introduced or exposed by a dependency change must be documented and dispositioned.

## 9. Required Automated Checks

Applicable automated checks may include dependency installation, dependency/security audit, ESLint, TypeScript type checking, build/compile validation, unit tests, integration tests, CodeQL/security scanning, and repository-specific quality checks.

A failed required check must be investigated.

Do not disable, bypass, suppress, or convert a failing required check into a passing result merely to merge a pull request. Any exception must be explicitly documented and approved.

## 10. Testing Expectations

Code complete does not equal production ready.

Before closure, the Jira issue must contain sufficient evidence of applicable validation. This may include automated test results, build results, workflow links, screenshots, smoke-test results, regression-test results, QA evidence, and deployment validation.

Failed testing must link to a defect or remediation item.

## 11. Review and Merge Expectations

- Required reviews and automated checks must complete before merge.
- A successful compile alone is not sufficient for acceptance.
- Developers should not rely solely on their own manual validation when independent review or QA is required.
- Do not merge around a known blocking failure.
- Emergency or hotfix changes must follow the documented hotfix path and receive post-deployment validation.

## 12. Change Scope and Architecture

Do not remove, redesign, or materially alter working functionality merely to solve an unrelated issue.

If implementation requires a significant architecture change, data-model change, authentication change, infrastructure change, payment change, security-control change, substantial new dependency, or breaking API behavior, raise the dependency or design decision before proceeding unless it is already authorized in Jira.

## 13. Jira Closure

A development issue should not be closed solely because code has been written.

Before closure, confirm as applicable:

- the PR is linked;
- required checks passed;
- required testing is complete;
- failed tests have disposition;
- the correct environment contains the change;
- known technical debt is documented;
- Product approval is complete where required.

## 14. Governance

These standards are governed through Jira issue **DEV-1278 — Establish Jira-to-GitHub Pull Request and Commit Traceability Governance**.

Changes to this standard should be made through a traceable pull request and corresponding Jira work item.
