# Code of Conduct Standard

This document defines the standard template for the CODE_OF_CONDUCT file required in every Core Red repository. Projects **must** include a `CODE_OF_CONDUCT.md` at the repository root that conforms to this standard.

The code of conduct is a behavioral contract, not an aspirational document. It defines enforceable expectations and consequences. Every section exists to eliminate ambiguity in what is expected, what is prohibited, and what happens when those boundaries are violated.

---

## Template Structure

The CODE_OF_CONDUCT file **must** contain the following sections, in this order:

1. Purpose
2. Scope
3. Expected Behavior
4. Unacceptable Behavior
5. Reporting
6. Enforcement
7. Attribution

---

## Section Requirements

### Purpose

State the intent of the code of conduct. The purpose section **must** declare that the document establishes behavioral expectations for all participants in the project, including contributors, maintainers, and anyone interacting within project spaces.

This section **must not** contain aspirational language, community-building rhetoric, or motivational statements. The purpose is structural: it defines what the document is, whom it applies to, and why it exists.

### Scope

Define where the code of conduct applies. The scope **must** include all of the following:

- All repository interactions (issues, pull requests, code review, discussions)
- All communication channels associated with the project (chat, forums, mailing lists)
- Public representations of the project (conferences, social media, blog posts)
- Private communications directly related to project business

The scope statement **must** make clear that violations in any of these contexts are subject to enforcement.

### Expected Behavior

Define the behaviors required of all participants. The following expectations **must** be stated:

- Communicate with professionalism and respect.
- Provide constructive, specific, and actionable feedback.
- Accept constructive criticism without hostility.
- Prioritize the technical merit of contributions over personal preference.
- Respect differing viewpoints, experience levels, and backgrounds.
- Exercise empathy and consideration in interactions.
- Focus on what is best for the project.

Each item **must** be presented as a bullet point. The section **must** be phrased as obligations, not suggestions.

### Unacceptable Behavior

Define behaviors that are prohibited. The following **must** be explicitly listed:

- Harassment, intimidation, or threats of any kind.
- Discriminatory language or conduct based on personal characteristics including but not limited to age, disability, ethnicity, gender identity, nationality, race, religion, or sexual orientation.
- Personal attacks, insults, or derogatory comments.
- Trolling, inflammatory comments, or sustained disruption of discussions.
- Publication of private information (addresses, emails, phone numbers) without explicit consent.
- Unwelcome sexual attention or advances.
- Advocating for or encouraging any of the above behaviors.
- Any conduct that a reasonable person would consider inappropriate in a professional setting.

Each item **must** be stated as a declarative prohibition without qualifying language. Do not use phrasing like "try to avoid" or "consider whether." The items are prohibitions, not requests.

### Reporting

Define how violations are reported. This section **must** include:

- A designated email address for reports. The canonical default is `<CONDUCT_EMAIL>`. Projects **must** replace this placeholder with an address from the official contact channels.
- A statement that all reports are treated confidentially.
- A statement that reporters will not face retaliation for good-faith reports.
- A statement that reports through public channels (issues, discussions) are not accepted for conduct violations.

Define what a report **must** include:

- The nature of the violation.
- The context in which it occurred (link, channel, timestamp).
- Any supporting evidence or screenshots.
- Whether the reporter wishes to remain anonymous.

This section **must not** include informal channels (e.g., direct messages, social media) as reporting mechanisms.

### Enforcement

Define the consequences of violations. This section **must** include the following enforcement actions, presented as a graduated response:

| Level | Action | Description |
|---|---|---|
| 1. Warning | Private notice | A private written notice identifying the violation and the expected correction. The participant is expected to comply immediately. |
| 2. Temporary Restriction | Temporary ban | Temporary removal from project interaction channels for a defined period. Further violations during the restriction period result in escalation. |
| 3. Permanent Ban | Permanent removal | Permanent removal from all project spaces and revocation of contribution rights. No appeal is available for this action. |

The enforcement section **must** state that:

- The severity of response is determined by the maintainers based on the nature, frequency, and context of the violation.
- Maintainers are obligated to enforce the code of conduct consistently.
- Maintainers who fail to enforce the code of conduct in good faith may themselves be subject to enforcement action by other project leadership.

### Attribution

State that the code of conduct is maintained as part of the Core Red standards. Include a reference to the Core Red Standards repository.

---

## Canonical Template

The following is the canonical CODE_OF_CONDUCT template. Projects **must** use this template, replacing only the designated placeholder fields.

```markdown
# Code of Conduct

## Purpose

This Code of Conduct establishes behavioral expectations for all participants in the <PROJECT_NAME> project. It applies to all contributors, maintainers, and anyone interacting within project spaces.

This is a behavioral contract. Participation in the project constitutes acceptance of these terms.

## Scope

This Code of Conduct applies to:

- All interactions within the project repository (issues, pull requests, code review, discussions)
- All communication channels associated with the project
- Public representations of the project by any participant
- Private communications directly related to project business

Violations in any of these contexts are subject to enforcement.

## Expected Behavior

All participants must:

- Communicate with professionalism and respect
- Provide constructive, specific, and actionable feedback
- Accept constructive criticism without hostility
- Prioritize the technical merit of contributions over personal preference
- Respect differing viewpoints, experience levels, and backgrounds
- Exercise empathy and consideration in interactions
- Focus on what is best for the project

## Unacceptable Behavior

The following behaviors are prohibited:

- Harassment, intimidation, or threats of any kind
- Discriminatory language or conduct based on personal characteristics including but not limited to age, disability, ethnicity, gender identity, nationality, race, religion, or sexual orientation
- Personal attacks, insults, or derogatory comments
- Trolling, inflammatory comments, or sustained disruption of discussions
- Publication of private information without explicit consent
- Unwelcome sexual attention or advances
- Advocating for or encouraging any of the above behaviors
- Any conduct that a reasonable person would consider inappropriate in a professional setting

## Reporting

To report a violation, send an email to:

`<CONDUCT_EMAIL>`

Include the following in the report:

- The nature of the violation
- The context in which it occurred (link, channel, timestamp)
- Any supporting evidence or screenshots
- Whether you wish to remain anonymous

All reports are treated confidentially. Reporters will not face retaliation for good-faith reports.

Do not report conduct violations through public channels (issues, discussions, pull requests).

## Enforcement

Maintainers will respond to violations with graduated enforcement:

1. **Warning** — A private written notice identifying the violation and expected correction. Immediate compliance is expected.
2. **Temporary Restriction** — Temporary removal from project interaction channels for a defined period. Further violations during the restriction period result in escalation.
3. **Permanent Ban** — Permanent removal from all project spaces and revocation of contribution rights.

The severity of response is determined by the maintainers based on the nature, frequency, and context of the violation. Maintainers are obligated to enforce this code consistently.

## Attribution

This Code of Conduct is defined by the Core Red Standards maintained by the Sxnnyside Project.
```

---

## Placeholder Fields

| Placeholder | Description |
|---|---|
| `<PROJECT_NAME>` | The display name of the project. Do not use the repository slug. |
| `<CONDUCT_EMAIL>` | The contact email for conduct violation reports. **Must** be one of the canonical contact channels. Default: `support.sxnnyside@sxnnysideproject.com`. |

---

## Official Contact Channels

The following are the only permitted email addresses for conduct reporting across Core Red projects:

- `security.sxnnyside@sxnnysideproject.com` — Security-related reports.
- `support.sxnnyside@sxnnysideproject.com` — General conduct and support reports.
- `legal.sxnnyside@sxnnysideproject.com` — Legal and compliance matters.
- `houjou.sxnnyside@sxnnysideproject.com` — Escalation to project leadership.

No other email addresses **may** be used in the reporting section. Projects **must not** invent additional contact addresses.

---

## Compliance

A CODE_OF_CONDUCT file is non-compliant if any of the following conditions are true:

- The file is absent from the repository root.
- Any required section is missing or incomplete.
- The reporting mechanism is absent or uses an informal channel.
- The reporting section does not define what a report must include.
- The reporting email is not from the official contact channels.
- The enforcement section lacks graduated response levels.
- The unacceptable behavior section uses qualifying or softening language.
- The tone contains aspirational, motivational, or community-building language.
- Placeholder fields have not been replaced with project-specific values.

Non-compliance **must** be resolved before release.