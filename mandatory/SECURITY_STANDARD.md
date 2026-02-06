# Security Standard

This document defines the standard template for the SECURITY file required in every Core Red repository. Projects **must** include a `SECURITY.md` at the repository root that conforms to this standard.

---

## Template Structure

The SECURITY file **must** contain the following sections, in this order:

1. Supported Versions
2. Reporting a Vulnerability
3. Security Considerations
4. Known Security Limitations
5. Best Practices
6. Threat Model
7. Security Updates

---

## Section Requirements

### Supported Versions

State whether the project is in active development or stable release. Provide a table listing the versions that currently receive security updates.

The table **must** use the following format:

```markdown
| Version | Supported |
|---|---|
| vX.Y.x | Yes |
| vX.Z.x | No |
```

- Use `Yes` or `No` to indicate support status. Emojis are not permitted.
- Only include versions that have been released.
- Remove end-of-life versions from the table or mark them explicitly as unsupported.

### Reporting a Vulnerability

This section **must** open with a statement that the project takes security seriously.

#### How to Report

This subsection **must** include:

- An explicit, bold instruction that vulnerabilities **must not** be reported through public issues.
- A designated reporting email address, presented in bold.
- The option to open a private security advisory on GitHub, with the full advisory URL provided.

#### What to Include

Define the information the reporter **should** include. The following items **must** be listed as an ordered list:

1. **Description**: Clear description of the vulnerability.
2. **Impact**: Potential impact and affected versions.
3. **Reproduction**: Step-by-step instructions to reproduce the vulnerability.
4. **Proof of Concept**: Code or example demonstrating the issue.
5. **Suggested Fix**: Recommendations for remediation, if available.

#### Response Timeline

Define the expected response timeline. The following commitments **must** be stated:

- **Initial Response**: Within 48 hours.
- **Status Update**: Within 7 days.
- **Fix Timeline**: Depending on severity, typically within 30 days.

#### Disclosure Policy

This subsection **must** state:

- The reporter **should** allow the maintainers time to fix the vulnerability before public disclosure.
- The maintainers will credit the reporter in the security advisory, unless the reporter prefers to remain anonymous.
- The maintainers **may** request the reporter's assistance in validating the fix.

### Security Considerations

This section **must** document the project's security-relevant properties and boundaries. It provides context for what the project does and does not guarantee from a security perspective.

The section **must** be organized into subsections that correspond to the project's architecture. Each subsection **must** describe the relevant security properties using a bulleted list.

Applicable subsection topics include, but are not limited to:

- **Input Handling** — How the project processes external input, including size limits, validation, encoding, and whether code execution occurs.
- **Application Permissions** — What system-level permissions the application requires (e.g., clipboard access, filesystem access, network access) and what it explicitly does not require.
- **Dependencies** — How external dependencies are managed and updated, including pinning strategies and update mechanisms.

Projects **must** include all subsections that are applicable to their architecture. Subsections that do not apply **may** be omitted.

### Known Security Limitations

This section **must** document known behaviors that could have security implications but are not vulnerabilities. Each limitation **must** be presented as a numbered subsection with a descriptive title.

Each limitation entry **must** include:

- A description of the behavior.
- An explanation of the risk, if any.
- Guidance to users on how to mitigate the risk.

This section **must not** understate risk or use hedging language. If a limitation exists, it **must** be stated directly.

### Best Practices

This section **must** provide security recommendations for both users and contributors or integrators of the project.

It **must** be divided into two subsections:

#### For Users

An ordered list of security practices for end users of the project. These **must** be actionable and specific.

#### For Developers

An ordered list of security practices for developers integrating or extending the project. These **must** cover input validation, error handling, size limits, and dependency management.

### Threat Model

This section **must** define what is in scope and out of scope for the project's security posture.

It **must** be divided into two subsections:

#### In Scope

A bulleted list of vulnerability categories that the project considers security-relevant and will address.

#### Out of Scope

A bulleted list of concerns that fall outside the project's security responsibility. Each entry **must** include a brief justification (e.g., "user responsibility", "expected behavior").

### Security Updates

Define how security updates are communicated. This section **must** list the announcement channels, presented as an ordered list. At minimum, the following channels **must** be included:

1. GitHub Security Advisories
2. Release notes in CHANGELOG
3. GitHub Releases page

State that critical security updates will be backported to supported versions when feasible.

---

## Canonical Template

```markdown
# Security Policy

## Supported Versions

[PROJECT_NAME] is currently in active development. Security updates will be provided for the following versions:

| Version | Supported |
|---|---|
| [VERSION] | Yes |

## Reporting a Vulnerability

We take security seriously. If you discover a security vulnerability in [PROJECT_NAME], report it responsibly.

### How to Report

**DO NOT** open a public issue for security vulnerabilities.

Instead, email security concerns to:

**[SECURITY_EMAIL]**

Or open a private security advisory on GitHub:
[ADVISORY_URL]

### What to Include

When reporting a vulnerability, include:

1. **Description**: Clear description of the vulnerability
2. **Impact**: Potential impact and affected versions
3. **Reproduction**: Step-by-step instructions to reproduce
4. **Proof of Concept**: Code or example demonstrating the issue
5. **Suggested Fix**: If you have ideas on how to fix it

### Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 7 days
- **Fix Timeline**: Depending on severity, typically within 30 days

### Disclosure Policy

- Allow the maintainers time to fix the vulnerability before public disclosure
- We will credit you in the security advisory (unless you prefer to remain anonymous)
- We may request your help in validating the fix

## Security Considerations

### [SUBSECTION_TITLE]

[Describe the security-relevant properties of this component.]

- [Security property or boundary]
- [Security property or boundary]
- [Security property or boundary]

### Dependencies

We regularly update dependencies to address known vulnerabilities:

- [DEPENDENCY_MANAGEMENT_DETAILS]

## Known Security Limitations

### 1. [LIMITATION_TITLE]

[Description of the behavior and its security implications.]

[Guidance for users on how to mitigate the risk.]

## Best Practices

### For Users

1. **Review Output**: Always review generated output before execution
2. **Trusted Sources**: Only process input from trusted sources
3. **Update Regularly**: Keep [PROJECT_NAME] updated to the latest version
4. **Sandboxed Execution**: Execute untrusted output in isolated environments

### For Developers

1. **Input Validation**: Always validate input before passing to [PROJECT_NAME]
2. **Size Limits**: Use appropriate maximum input sizes for your use case
3. **Error Handling**: Handle all errors returned by the API
4. **Update Dependencies**: Regularly update [PROJECT_NAME] and its dependencies

## Threat Model

### In Scope

- Input processing vulnerabilities
- Memory safety issues
- Dependency vulnerabilities
- Output integrity

### Out of Scope

- Execution of generated output (user responsibility)
- Denial of service via legitimate large inputs
- Social engineering attacks
- Physical access to the user's machine

## Security Updates

Security updates will be announced via:

1. GitHub Security Advisories
2. Release notes in CHANGELOG.md
3. GitHub Releases page

Critical security updates will be backported to supported versions when feasible.
```

---

## Placeholder Fields

| Field | Description |
|---|---|
| `[PROJECT_NAME]` | The display name of the project. |
| `[VERSION]` | The currently supported version(s). Add rows as needed. |
| `[SECURITY_EMAIL]` | The designated security reporting email. For Core Red projects, use `security.sxnnyside@sxnnysideproject.com`. |
| `[ADVISORY_URL]` | The full URL to the GitHub security advisories page. |
| `[SUBSECTION_TITLE]` | A descriptive title for each security considerations subsection (e.g., "Input Handling", "Desktop Application"). |
| `[DEPENDENCY_MANAGEMENT_DETAILS]` | Description of how each dependency category is managed and updated. |
| `[LIMITATION_TITLE]` | A descriptive title for each known limitation entry. |

---

## Compliance

A SECURITY file is non-compliant if any of the following conditions are true:

- The file is absent from the repository root.
- The supported versions table is missing or empty.
- The reporting instructions direct reporters to public channels.
- The reporting email address is not provided.
- The response timeline is absent or undefined.
- The disclosure policy is absent.
- The security considerations section is missing or does not reflect the project's architecture.
- The known security limitations section is absent when known limitations exist.
- The best practices section is absent.
- The threat model section is absent or does not define in-scope and out-of-scope boundaries.
- The security updates announcement channels are not listed.
- The tone deviates from the neutral, professional standard defined by Core Red rules.

Non-compliance **must** be resolved before release.