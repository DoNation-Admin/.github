# DoNation Security Policy

## Security Handling Standard

DoNation treats security findings, credentials, access tokens, and sensitive configuration as controlled information.

## Do Not Publish Sensitive Details

Do not place passwords, API keys, AWS credentials, GitHub tokens, Twilio secrets, database credentials, private keys, authentication secrets, OTP values, customer/member sensitive data, detailed exploit instructions for unresolved vulnerabilities, production secrets, or confidential infrastructure details in public repository content, pull request descriptions, issues, comments, screenshots, or logs.

## Reporting a Security Issue

Do not open a public GitHub issue containing exploit details or sensitive information.

Report the issue through the approved internal DoNation security/engineering path and create the appropriate restricted Jira remediation item when authorized.

Include the affected repository/component, observed behavior, severity/impact information available, reproduction details appropriate for internal handling, affected versions/commits if known, and recommended containment or remediation if known.

## Accidental Secret Exposure

If a secret is committed or exposed:

1. Treat the secret as compromised.
2. Notify the appropriate DoNation owner immediately.
3. Rotate/revoke the credential.
4. Remove the exposed value from active use.
5. Create a traceable remediation record.
6. Evaluate whether Git history cleanup is required.
7. Validate that replacement credentials are stored using approved secret management.

Deleting a secret from the latest commit does not make the previous exposure safe.

## Dependency and Code-Scanning Findings

Security findings from CodeQL, dependency scanning, secret scanning, or similar tools must be reviewed and dispositioned.

Do not disable or suppress a security check merely to obtain a passing pull request.

Unresolved launch-impacting findings must have a Jira owner and documented disposition before release approval.
