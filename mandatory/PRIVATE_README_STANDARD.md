# Private README Standard

This document defines the standard template for the README file in private or internal Core Red repositories. Projects **must** include a `README.md` at the repository root that conforms to this standard.

The private README serves the same structural purpose as the public README: it defines the project's identity, communicates its purpose, establishes how to install and use it, and directs the reader to all other project documentation. The difference is audience. The private README is written for internal contributors and operators, not external users.

This standard applies only to repositories that are not publicly accessible. For public repositories, see [PUBLIC_README_STANDARD.md](PUBLIC_README_STANDARD.md).

---

## Relationship to the Public README Standard

The private README standard shares the same section ordering, structural requirements, and density expectations as the public README standard. This document defines only the differences. For any requirement not explicitly overridden here, the [PUBLIC_README_STANDARD.md](PUBLIC_README_STANDARD.md) applies.

The following sections are identical to the public standard and are not redefined here:

- Header Block
- About (including Philosophy subsection)
- Features
- Installation (including Prerequisites and Installation Methods)
- Usage (including CLI, Desktop App, As a Library, Web Interface subsections)
- Architecture (including inline and external modes)
- Project Status (including Roadmap)
- License
- Footer Block

Refer to [PUBLIC_README_STANDARD.md](PUBLIC_README_STANDARD.md) for the full specification of these sections.

---

## Sections Modified for Private Repositories

### Contributing

The Contributing section in a private README **must** contain:

- A statement directing contributors to `CONTRIBUTING.md`.
- A statement directing contributors to `CODE_OF_CONDUCT.md`.
- A statement identifying who has write access or how access is granted.

Both file references **must** be Markdown links.

This section **may** additionally reference internal processes such as:

- Internal issue trackers or project boards.
- Team communication channels (by name, not by URL or invite link).
- Approval workflows specific to the organization.

These references **must** remain factual and procedural. They **must not** include credentials, tokens, or access URLs.

### Operational Notes (conditional)

Private READMEs **may** include an **Operational Notes** section (H2) placed after Project Status and before Contributing. This section is not permitted in public READMEs.

When present, the Operational Notes section **may** include:

- Deployment procedures or references to deployment documentation.
- Environment-specific configuration requirements.
- Known operational constraints or dependencies.
- References to internal monitoring, logging, or alerting systems (by name, not by URL).
- On-call or escalation procedures (referencing roles, not individuals).

Each item **must** be presented as a subsection (H3) or a bulleted list, depending on complexity.

The Operational Notes section **must** adhere to all DOCUMENT_TONE rules. Internal context does not relax the tone requirements.

---

## Template Structure

The README for private repositories **must** contain the following sections, in this order. Sections marked as conditional follow the same rules as in the public standard unless overridden above.

1. Header Block
2. About
3. Features
4. Installation
5. Usage (conditional)
6. Architecture (conditional)
7. Project Status
8. Operational Notes (conditional: private only)
9. Contributing
10. License
11. Footer Block

---

## Canonical Template

The canonical template is identical to the public README template with the following modifications:

- The Contributing section includes an access control statement.
- The Operational Notes section is included as an optional block.

```markdown
# <PROJECT_NAME>

<p align="center">
  <strong><PROJECT_TAGLINE></strong><br>
  <em><PROJECT_SUBTITLE></em>
</p>

<p align="center">
  <a href="#about">About</a> •
  <a href="#features">Features</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#architecture">Architecture</a> •
  <a href="#contributing">Contributing</a>
</p>

---

## About

**<PROJECT_NAME>** is <PROJECT_DESCRIPTION>.

<CONTEXT_PARAGRAPH>

### Philosophy

> *"<PHILOSOPHY_QUOTE>"*

<PHILOSOPHY_EXPANSION>

This is a **Core Red** project, part of <ORGANIZATIONAL_CONTEXT>.

## Features

- **<FEATURE_1_LABEL>**: <FEATURE_1_DESCRIPTION>
- **<FEATURE_2_LABEL>**: <FEATURE_2_DESCRIPTION>
  - <SUB_FEATURE_DESCRIPTION>
  - <SUB_FEATURE_DESCRIPTION>
- **<FEATURE_3_LABEL>**: <FEATURE_3_DESCRIPTION>
- **<FEATURE_4_LABEL>**: <FEATURE_4_DESCRIPTION>

## Installation

### Prerequisites

- [<RUNTIME>](<RUNTIME_INSTALL_URL>) (<VERSION_CONSTRAINT>)
- [<TOOL>](<TOOL_INSTALL_URL>) (<VERSION_CONSTRAINT>)

### From Source

\`\`\`bash
# Clone the repository
git clone <REPOSITORY_URL>
cd <PROJECT_DIRECTORY>

# Build the project
<BUILD_COMMAND>

# The binary will be at <BINARY_LOCATION>
\`\`\`

### <ADDITIONAL_INSTALL_METHOD>

\`\`\`bash
# <INSTALL_STEP_DESCRIPTION>
<INSTALL_COMMAND>
\`\`\`

## Usage

### CLI

\`\`\`bash
# Basic usage
<BASIC_CLI_COMMAND>

# <OPTION_DESCRIPTION>
<CLI_COMMAND_WITH_OPTIONS>

# <OPTION_DESCRIPTION>
<CLI_COMMAND_WITH_OPTIONS>
\`\`\`

### Desktop App

1. Launch <PROJECT_NAME>
2. <USER_ACTION_STEP>
3. <USER_ACTION_STEP>
4. <USER_ACTION_STEP>

### As a Library

\`\`\`<LANGUAGE_ID>
<IMPORT_STATEMENT>

// Basic usage
<LIBRARY_USAGE_EXAMPLE>

// With custom options
<LIBRARY_ADVANCED_EXAMPLE>
\`\`\`

## Architecture

\`\`\`
<PROJECT_DIRECTORY>/
├── <DIRECTORY>/         # <DESCRIPTION>
│   └── <SUBDIRECTORY>/
│       ├── <FILE>       # <DESCRIPTION>
│       └── <FILE>       # <DESCRIPTION>
│
├── <DIRECTORY>/         # <DESCRIPTION>
│   ├── <SUBDIRECTORY>/  # <DESCRIPTION>
│   └── <SUBDIRECTORY>/  # <DESCRIPTION>
│
└── <DIRECTORY>/         # <DESCRIPTION>
\`\`\`

### Stack

| Component | Technology |
|---|---|
| <COMPONENT_NAME> | <TECHNOLOGY_NAME> |
| <COMPONENT_NAME> | <TECHNOLOGY_NAME> |
| <COMPONENT_NAME> | <TECHNOLOGY_NAME> |

## Project Status

**Current Version**: <VERSION> (<STABILITY_LEVEL>)

<STATUS_STATEMENT>

### Roadmap

- [x] <COMPLETED_MILESTONE>
- [x] <COMPLETED_MILESTONE>
- [ ] <PENDING_MILESTONE>
- [ ] <PENDING_MILESTONE>

## Operational Notes

### Deployment

<DEPLOYMENT_PROCEDURE_OR_REFERENCE>

### Environment Configuration

<ENVIRONMENT_SPECIFIC_REQUIREMENTS>

### Known Constraints

- <OPERATIONAL_CONSTRAINT>
- <OPERATIONAL_CONSTRAINT>

## Contributing

Contributions are accepted. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Before contributing, read the [Code of Conduct](CODE_OF_CONDUCT.md).

Repository write access is managed by <ACCESS_AUTHORITY>. Contact <ACCESS_CONTACT_METHOD> to request access.

## License

This project is licensed under the <LICENSE_NAME> — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <strong><PROJECT_NAME></strong> — A Core Red Project<br>
  <em>&copy; <YEAR> <ORGANIZATION_NAME></em>
</p>
```

---

## Additional Placeholder Fields

The private README template uses all placeholder fields defined in [PUBLIC_README_STANDARD.md](PUBLIC_README_STANDARD.md), plus the following:

| Placeholder | Description |
|---|---|
| `<DEPLOYMENT_PROCEDURE_OR_REFERENCE>` | A description of or link to the deployment procedure. |
| `<ENVIRONMENT_SPECIFIC_REQUIREMENTS>` | Environment-specific configuration or dependency requirements. |
| `<OPERATIONAL_CONSTRAINT>` | A known operational constraint or dependency. |
| `<ACCESS_AUTHORITY>` | The role or team responsible for repository access (e.g., "the project maintainer", "the infrastructure team"). |
| `<ACCESS_CONTACT_METHOD>` | The method for requesting access (e.g., "the team lead", "an internal access request"). Do not embed URLs or credentials. |

---

## Compliance

A README file in a private repository is non-compliant if any of the following conditions are true:

- The file is absent from the repository root.
- The header block is missing or does not include the tagline, subtitle, and navigation bar.
- The About section does not define the project or lacks the Philosophy subsection.
- The Features section is absent or uses prose instead of a structured list.
- The Installation section does not include prerequisites and at least one installation method with complete commands.
- The Usage section is absent when the project has a user-facing interface.
- The Architecture section is absent or does not use one of the two defined modes (inline or external).
- The Project Status section does not state the current version and stability level.
- The Contributing section does not link to CONTRIBUTING.md and CODE_OF_CONDUCT.md.
- The License section does not state the license and link to the LICENSE file.
- The footer block is missing.
- The Operational Notes section contains credentials, tokens, or access URLs.
- The tone contains marketing, motivational, or emotional language.
- Placeholder fields have not been replaced with project-specific values.

Non-compliance **must** be resolved before release.