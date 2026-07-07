# Security Policy

## Reporting Vulnerabilities

**Do not open a GitHub issue to report security vulnerabilities.**

If you believe you have found a security vulnerability, you can report it privately via either of these channels:

**GitHub**: Use [Report a vulnerability](https://github.com/phemehq/pheme/security/advisories/new) (preferred)

Include the following in your report:

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Proof of concept (if available)

You will receive an acknowledgment within 48 hours. Once confirmed, critical vulnerabilities will be fixed within 90 days and all others within 180 days. You will be notified when a fix is released, and credited for the disclosure if desired.

**Do not disclose the vulnerability publicly until a fix has been released.**

## Secure Development Practices

- All changes are reviewed before merging
- Dependencies are regularly audited for known vulnerabilities
- All commits must carry a DCO sign-off (`git commit -s`); see CONTRIBUTING.md
- GPG-signed commits (`git commit -S`) are encouraged for maintainers
- No secrets, API keys, or credentials are committed to the repository
- Security-relevant functionality is covered by tests

## Security Updates

Security fixes are released as versioned updates. Users should:

- Keep dependencies up to date
- Monitor [GitHub releases](https://github.com/phemehq/pheme/releases) for security patches
- Review the `CHANGELOG.md` for security-related changes

## Deployment Guidance

When deploying Pheme:

- Follow the principle of least privilege for Kubernetes RBAC policies
- Use environment variables for all sensitive configuration (LLM API keys, database passwords)
- Mount credentials as read-only volumes or secrets
- Rotate the API bearer token periodically
- Run behind a reverse proxy with TLS in production
- Enable audit logging for Prometheus and K8s API access
- Monitor Pheme service logs for security-related errors

## Non-Vulnerability Suggestions

Security feature requests and improvement suggestions are welcome as [GitHub issues](https://github.com/phemehq/pheme/issues/new).
