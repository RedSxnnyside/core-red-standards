# Public README Standard

This document defines the standard template for the README file in public Core Red repositories. Projects **must** include a `README.md` at the repository root that conforms to this standard.

The README is the first document a user encounters. It defines the project's identity, communicates its purpose, establishes how to install and use it, and directs the reader to all other project documentation. The README is not a summary. It is the project's operational front page.

This standard applies only to publicly accessible repositories. For private or internal repositories, see [PRIVATE_README_STANDARD.md](PRIVATE_README_STANDARD.md).

---

## Template Structure

The README for public repositories **must** contain the following sections, in this order. Sections marked as conditional **may** be omitted only when the stated condition applies.

1. Header Block
2. About
3. Features
4. Installation
5. Usage (conditional: omit only if the project has no user-facing interface)
6. Architecture (conditional: see Architecture Handling below)
7. Project Status
8. Contributing
9. License
10. Footer Block

---

## Section Requirements

### Header Block

The README **must** begin with an H1 heading containing the project name, followed by a centered block that includes:

- A bold tagline (one sentence describing the project's function).
- An italicized subtitle identifying the project as a Core Red project or its organizational affiliation.
- A navigation bar linking to major sections within the document.

The header block uses HTML `<p align="center">` for centering. This is the only context in which inline HTML is permitted in Core Red documentation.

Format:

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
```

The navigation bar **must** link only to H2 sections that exist in the document. Remove links that correspond to omitted conditional sections.

### About

The About section **must** contain:

1. A **lead paragraph** that defines the project in one to three sentences. The lead paragraph **must** state what the project is, what it does, and what domain it operates in. The first mention of the project name **must** be bold.

2. A **context paragraph** that places the project within its technical domain. If the project implements or extends a known concept, that concept **must** be defined or linked here. Do not assume the reader knows the concept.

3. A **Philosophy subsection** (H3) containing a blockquote that captures the project's design philosophy in one sentence, followed by a paragraph that expands on it. The philosophy **must** describe the project's design values (e.g., minimalism, precision, composability) without using marketing language. State that the project is a Core Red project and identify the organizational context.

### Features

The Features section **must** present the project's capabilities as a bulleted list. Each top-level bullet **must** be a bold label followed by a colon and a concise description. Sub-bullets are permitted for enumerating variants or sub-capabilities.

Features **must** describe what the project does, not how it does it. Implementation details belong in Architecture.

Format:

```markdown
- **<FEATURE_LABEL>**: <FEATURE_DESCRIPTION>
  - <SUB_FEATURE_DESCRIPTION>
  - <SUB_FEATURE_DESCRIPTION>
```

### Installation

The Installation section **must** include:

#### Prerequisites

A bulleted list of all required tools, runtimes, and dependencies. Each item **must** be a linked tool name followed by a parenthesized version constraint.

Format:

```markdown
- [<TOOL_NAME>](<INSTALL_URL>) (<VERSION_CONSTRAINT>)
```

#### Installation Methods

At minimum one installation method **must** be provided. Each method **must** have its own H3 subsection with a descriptive heading and a complete fenced code block containing all commands required to install the project using that method.

Common method headings include but are not limited to:

- `From Source`
- `Via Package Manager`
- `CLI Only`
- `Desktop App`

Each code block **must** include inline comments explaining each step.

### Usage

The Usage section **must** document how to interact with the project. This section supports multiple optional subsections depending on the project's distribution model. At least one subsection **must** be present unless the project has no user-facing interface.

#### CLI (conditional)

Include this subsection if the project provides a command-line interface. Present usage examples as fenced `bash` code blocks. Each example **must** include an inline comment describing its purpose. Cover at minimum:

- Basic usage
- Common flags and options
- Input methods (stdin, arguments, files)

#### Desktop App (conditional)

Include this subsection if the project provides a graphical desktop application. Present usage as a numbered procedural list. Each step **must** describe a single user action and its expected result.

#### As a Library (conditional)

Include this subsection if the project is distributed as a library, SDK, or crate. Present usage examples as fenced code blocks in the appropriate language. Cover at minimum:

- Import or dependency declaration
- Basic invocation
- Configuration or customization

#### Web Interface (conditional)

Include this subsection if the project provides a web-based interface. Follow the same conventions as Desktop App.

When a subsection does not apply to the project, omit it entirely. Do not include empty subsections or subsections stating "not applicable."

### Architecture

This section documents the project's internal structure. Its handling depends on project complexity.

#### Inline Architecture (default)

For projects where the architecture can be communicated in a single section, include the architecture directly in the README. The section **must** contain:

1. A directory tree in a fenced code block showing the project's top-level structure. Each entry **must** include an inline comment describing its purpose.

2. A **Stack** subsection (H3) containing a table with at minimum two columns: Component and Technology.

Format:

```markdown
| Component | Technology |
|---|---|
| <COMPONENT_NAME> | <TECHNOLOGY_NAME> |
```

#### External Architecture (for larger systems)

If the project's architecture cannot be communicated in a single README section without exceeding reasonable length or complexity, the Architecture section **must** instead contain:

- A one-paragraph summary of the system's high-level structure.
- A link to `ARCHITECTURE.md` for full documentation.

The threshold for moving architecture to an external file is the author's judgment, but the following conditions **should** trigger it:

- The directory tree exceeds 30 lines.
- The system has more than 5 distinct components or services.
- The architecture requires diagrams or data flow descriptions.

### Project Status

The Project Status section **must** contain:

- A **Current Version** line in bold, stating the version and its stability level (e.g., Alpha, Beta, Stable).
- A brief statement of the project's development status (e.g., active development, maintenance mode, archived).
- A **Roadmap** subsection (H3) presented as a checklist. Completed items use `[x]` and pending items use `[ ]`.

Format:

```markdown
**Current Version**: <VERSION> (<STABILITY_LEVEL>)

<STATUS_STATEMENT>

### Roadmap

- [x] <COMPLETED_MILESTONE>
- [ ] <PENDING_MILESTONE>
```

### Contributing

The Contributing section **must** contain:

- A statement directing contributors to `CONTRIBUTING.md`.
- A statement directing contributors to `CODE_OF_CONDUCT.md`.

Both references **must** be Markdown links.

This section **must not** duplicate content from CONTRIBUTING.md. Its sole purpose is navigation.

### License

The License section **must** state the project's license and link to the LICENSE file.

Format:

```markdown
This project is licensed under the <LICENSE_NAME> — see the [LICENSE](LICENSE) file for details.
```

### Footer Block

The README **must** end with a centered footer block containing:

- The project name in bold.
- An organizational identification line (e.g., "A Core Red Project").
- A copyright line with the year and the organization name.

Format:

```markdown
<p align="center">
  <strong><PROJECT_NAME></strong> — A Core Red Project<br>
  <em>&copy; <YEAR> <ORGANIZATION_NAME></em>
</p>
```

---

## Architecture Handling

The README standard defines two modes for documenting architecture:

| Mode | Location | Condition |
|---|---|---|
| Inline | Within the README Architecture section | The project's structure can be communicated in a single section. |
| External | Separate `ARCHITECTURE.md` file | The project's structure exceeds the reasonable scope of a README section. |

Projects **must** use one of these two modes. Both modes are compliant. The choice is determined by the project's complexity, not by preference.

When architecture is external, the README Architecture section still **must** exist. It provides a summary and a link. It does not become an empty heading.

---

## Canonical Template

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

## Contributing

Contributions are accepted. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Before contributing, read the [Code of Conduct](CODE_OF_CONDUCT.md).

## License

This project is licensed under the <LICENSE_NAME> — see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <strong><PROJECT_NAME></strong> — A Core Red Project<br>
  <em>&copy; <YEAR> <ORGANIZATION_NAME></em>
</p>
```

---

## Placeholder Fields

| Placeholder | Description |
|---|---|
| `<PROJECT_NAME>` | The display name of the project. |
| `<PROJECT_TAGLINE>` | A one-sentence description of what the project does. |
| `<PROJECT_SUBTITLE>` | Organizational identification (e.g., "A Core Red Experimental Tool"). |
| `<PROJECT_DESCRIPTION>` | One to three sentences defining the project, its function, and its domain. |
| `<CONTEXT_PARAGRAPH>` | A paragraph placing the project in its technical domain, defining relevant concepts. |
| `<PHILOSOPHY_QUOTE>` | A one-sentence design philosophy quote. |
| `<PHILOSOPHY_EXPANSION>` | A paragraph expanding on the design philosophy without marketing language. |
| `<ORGANIZATIONAL_CONTEXT>` | Description of the organizational context (e.g., "an experimental toolkit for developers"). |
| `<FEATURE_N_LABEL>` | Bold label for a feature. |
| `<FEATURE_N_DESCRIPTION>` | Concise description of the feature's user-facing capability. |
| `<SUB_FEATURE_DESCRIPTION>` | Description of a feature variant or sub-capability. |
| `<RUNTIME>` | Primary language runtime name. |
| `<RUNTIME_INSTALL_URL>` | Installation URL for the primary runtime. |
| `<TOOL>` | Additional required tool name. Repeat as needed. |
| `<TOOL_INSTALL_URL>` | Installation URL for the additional tool. |
| `<VERSION_CONSTRAINT>` | Minimum version or version range constraint. |
| `<REPOSITORY_URL>` | The Git clone URL for the repository. |
| `<PROJECT_DIRECTORY>` | The directory name after cloning. |
| `<BUILD_COMMAND>` | The command to build the project. |
| `<BINARY_LOCATION>` | The path to the built binary or output artifact. |
| `<ADDITIONAL_INSTALL_METHOD>` | Heading for an additional installation method. Repeat as needed. |
| `<INSTALL_COMMAND>` | The command for the additional installation method. |
| `<BASIC_CLI_COMMAND>` | The most basic CLI invocation. |
| `<CLI_COMMAND_WITH_OPTIONS>` | A CLI invocation demonstrating a specific flag or option. |
| `<OPTION_DESCRIPTION>` | Inline comment describing the CLI option being demonstrated. |
| `<LANGUAGE_ID>` | The code block language identifier for library examples. |
| `<IMPORT_STATEMENT>` | The import or use statement for the library. |
| `<LIBRARY_USAGE_EXAMPLE>` | A minimal library usage example. |
| `<LIBRARY_ADVANCED_EXAMPLE>` | A library usage example with custom configuration. |
| `<COMPONENT_NAME>` | The name of an architectural component. |
| `<TECHNOLOGY_NAME>` | The technology used for the component. |
| `<VERSION>` | The current project version. |
| `<STABILITY_LEVEL>` | The stability level (Alpha, Beta, Stable). |
| `<STATUS_STATEMENT>` | A brief statement on the project's development status. |
| `<COMPLETED_MILESTONE>` | A completed roadmap item. |
| `<PENDING_MILESTONE>` | A pending roadmap item. |
| `<LICENSE_NAME>` | The name of the license (e.g., MIT License, Custom License). |
| `<YEAR>` | The copyright year. |
| `<ORGANIZATION_NAME>` | The copyright holder organization name. |

---

## Compliance

A README file in a public repository is non-compliant if any of the following conditions are true:

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
- The tone contains marketing, motivational, or emotional language.
- Placeholder fields have not been replaced with project-specific values.

Non-compliance **must** be resolved before release.