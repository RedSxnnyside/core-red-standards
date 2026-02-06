# Private Contributing Standard

This document defines the standard template for the CONTRIBUTING file in private or internal Core Red repositories. Projects **must** include a `CONTRIBUTING.md` at the repository root that conforms to this standard.

This standard applies only to repositories that are not publicly accessible. For public repositories, see [PUBLIC_CONTRIBUTING_STANDARD.md](PUBLIC_CONTRIBUTING_STANDARD.md).

The private CONTRIBUTING file mirrors the structure of the public standard but omits the fork-based workflow. Contributors clone and branch directly.

---

## Template Structure

The CONTRIBUTING file for private repositories **must** contain the following sections, in this order:

1. Table of Contents
2. Code of Conduct
3. Getting Started
4. Development Setup
5. How to Contribute
6. Code Review
7. Code Style
8. Commit Guidelines

---

## Section Requirements

### Table of Contents

A linked table of contents **must** appear immediately after the document title. It **must** include an anchor link to every H2 section in the document.

### Code of Conduct

Reference the project's CODE_OF_CONDUCT file. State that participation in the project requires adherence to the code of conduct. Link directly to `CODE_OF_CONDUCT.md`.

### Getting Started

Define the step-by-step procedure for beginning a contribution. The following steps **must** be presented as an ordered list:

1. Clone the repository.
2. Set up the development environment.
3. Create a branch for the changes.
4. Make the changes.
5. Test the changes.
6. Open a pull request and assign a reviewer.

### Development Setup

This section **must** include complete instructions for setting up a local development environment. It **must** be detailed enough for a contributor to build and test the project from a clean checkout.

#### Prerequisites

List all required tools with their minimum versions. Each tool **must** be presented as a bold label followed by a version constraint and an install link.

Format:

```markdown
- **[TOOL_NAME]** ([VERSION]+) - [Install]([INSTALL_URL])
```

Include access requirements (e.g., repository access granted by a maintainer).

#### Building

Provide the complete build instructions in a fenced code block. The block **must** include:

- Clone command
- Build command
- Test command
- Release build command (if applicable)

#### Additional Build Targets

If the project has additional build targets, each **must** be documented in a separate subsection with its own fenced code block.

### How to Contribute

This section **must** contain the following subsections.

#### Reporting Bugs

State that contributors **should** check existing issues before creating a bug report, to avoid duplicates.

Define what a bug report **must** include. The following items **must** be listed:

- **Clear title**: Descriptive summary of the issue.
- **Steps to reproduce**: Detailed steps to reproduce the behavior.
- **Expected behavior**: What the contributor expected to happen.
- **Actual behavior**: What actually happened.
- **Environment**: Operating system, runtime versions, and relevant tooling versions.
- **Screenshots**: If applicable.

#### Suggesting Features

Define what a feature suggestion **must** include:

- **Clear title**: Descriptive summary of the feature.
- **Use case**: Why the feature is needed.
- **Proposed solution**: How the contributor envisions the feature working.
- **Alternatives considered**: Other approaches that were evaluated.

#### Code Contributions

List the types of contributions that are accepted:

- Bug fixes
- Performance improvements
- Documentation improvements
- New features (contributors **must** open an issue for discussion before implementation)

### Code Review

Define the review process:

- Every pull request **must** be reviewed by at least one maintainer.
- The author **must not** merge their own pull request without approval.
- Maintainers **may** request changes, ask for clarification, or decline the contribution.
- Review comments **must** be specific, actionable, and professional.
- Contributors **must** address all review feedback before merge.
- Maintainers reserve the right to modify contributions before or after merge to ensure compliance.

### Code Style

This section **must** define the code style expectations for each language used in the project. Each language **must** have its own subsection.

Each language subsection **must** include:

- The applicable style guide or standard (linked, if external).
- The required formatting tool and its invocation command.
- The required linting tool and its invocation command.
- Key conventions specific to the project.
- A minimal, annotated code example demonstrating the expected style.

Code examples **must** be presented in fenced code blocks with the appropriate language identifier. They **must** show correct documentation comment style and function structure.

### Commit Guidelines

State that the project follows [Conventional Commits](https://www.conventionalcommits.org/).

#### Format

Provide the commit message format in a fenced code block:

```text
<type>(<scope>): <subject>

<body>

<footer>
```

#### Types

List all permitted commit types:

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

#### Examples

Provide at minimum three concrete commit message examples covering different types. Each example **must** be a realistic commit message in a fenced code block, demonstrating proper subject, body, and footer usage.

#### Rules

State the following commit message rules:

- Use imperative mood ("add" not "added").
- Do not capitalize the first letter of the subject.
- No period at the end of the subject.
- Limit the subject line to 50 characters.
- Wrap the body at 72 characters.

---

## Canonical Template

```markdown
# Contributing to [PROJECT_NAME]

This is a Core Red project. All contributions are subject to review, approval, and compliance with the project's standards.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [How to Contribute](#how-to-contribute)
- [Code Review](#code-review)
- [Code Style](#code-style)
- [Commit Guidelines](#commit-guidelines)

## Code of Conduct

This project adheres to a Code of Conduct. By participating, you are expected to uphold this code. Read [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) before contributing.

## Getting Started

1. Clone the repository
2. Set up the development environment
3. Create a branch for your changes
4. Make your changes
5. Test your changes
6. Open a pull request and assign a reviewer

## Development Setup

### Prerequisites

- **[RUNTIME]** ([VERSION]+) - [Install]([INSTALL_URL])
- **[BUILD_TOOL]** - [Install]([TOOL_INSTALL_URL])
- Repository access granted by a maintainer

### Building

\`\`\`bash
# Clone the repository
git clone [REPOSITORY_URL]
cd [PROJECT_DIRECTORY]

# Build the project
[BUILD_COMMAND]

# Run tests
[TEST_COMMAND]

# Build in release mode
[RELEASE_BUILD_COMMAND]
\`\`\`

## How to Contribute

### Reporting Bugs

Before creating a bug report, check existing issues to avoid duplicates.

When reporting a bug, include:

- **Clear title**: Descriptive summary of the issue
- **Steps to reproduce**: Detailed steps to reproduce the behavior
- **Expected behavior**: What you expected to happen
- **Actual behavior**: What actually happened
- **Environment**: OS, runtime versions
- **Screenshots**: If applicable

### Suggesting Features

Feature suggestions are accepted. Provide:

- **Clear title**: Descriptive summary of the feature
- **Use case**: Why this feature would be useful
- **Proposed solution**: How you envision the feature working
- **Alternatives considered**: Other solutions you have evaluated

### Code Contributions

We accept contributions for:

- Bug fixes
- Performance improvements
- Documentation improvements
- New features (discuss first via an issue)

## Code Review

- Every pull request must be reviewed by at least one maintainer.
- The author must not merge their own pull request without approval.
- Maintainers may request changes, ask for clarification, or decline the contribution.
- Review comments must be specific, actionable, and professional.
- Address all review feedback before merge.

## Code Style

### [LANGUAGE]

- Follow the [LANGUAGE Style Guide]([STYLE_GUIDE_URL])
- Use `[FORMATTER]` for formatting: `[FORMAT_COMMAND]`
- Use `[LINTER]` for linting: `[LINT_COMMAND]`
- Write documentation comments for public APIs
- Keep functions focused and small

\`\`\`[LANGUAGE_ID]
// Example: proper documentation and function structure
[CODE_EXAMPLE]
\`\`\`

## Commit Guidelines

We follow [Conventional Commits](https://www.conventionalcommits.org/).

### Format

\`\`\`text
<type>(<scope>): <subject>

<body>

<footer>
\`\`\`

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

### Examples

\`\`\`text
feat(core): add Unicode escape strategy

Implements Unicode escape sequences for handling
special characters in output.

Closes #123
\`\`\`

\`\`\`text
fix(ui): correct copy button state after clipboard write

The copy button now properly resets its state after the
clipboard operation completes.
\`\`\`

\`\`\`text
docs: update installation instructions for Windows
\`\`\`

### Rules

- Use imperative mood ("add" not "added")
- Do not capitalize the first letter
- No period at the end of the subject
- Limit subject line to 50 characters
- Wrap body at 72 characters
```

---

## Placeholder Fields

| Field | Description |
|---|---|
| `[PROJECT_NAME]` | The display name of the project. |
| `[RUNTIME]` | The primary language runtime (e.g., Rust, Node.js, Python). |
| `[VERSION]` | The minimum required runtime version. |
| `[INSTALL_URL]` | The installation URL for the primary runtime. |
| `[BUILD_TOOL]` | Additional required build tool. Repeat as needed. |
| `[TOOL_INSTALL_URL]` | The installation URL for the build tool. |
| `[REPOSITORY_URL]` | The Git clone URL for the repository. |
| `[PROJECT_DIRECTORY]` | The directory name after cloning. |
| `[BUILD_COMMAND]` | The command to build the project. |
| `[TEST_COMMAND]` | The command to run the test suite. |
| `[RELEASE_BUILD_COMMAND]` | The command to build in release mode. |
| `[LANGUAGE]` | The name of each language used (one subsection per language). |
| `[LANGUAGE_ID]` | The code block language identifier. |
| `[STYLE_GUIDE_URL]` | URL of the applicable style guide. |
| `[FORMATTER]` | The formatting tool name. |
| `[FORMAT_COMMAND]` | The command to run the formatter. |
| `[LINTER]` | The linting tool name. |
| `[LINT_COMMAND]` | The command to run the linter. |
| `[CODE_EXAMPLE]` | A minimal, annotated code example for the language. |

---

## Compliance

A CONTRIBUTING file in a private repository is non-compliant if any of the following conditions are true:

- The file is absent from the repository root.
- The table of contents is missing or incomplete.
- The code of conduct is not referenced.
- The getting started procedure is absent.
- The development setup does not include prerequisites, build, and test instructions.
- The how to contribute section does not define bug reporting, feature suggestion, and code contribution subsections.
- The code review process is absent or does not prohibit self-merging.
- The code style section does not include per-language conventions with formatting and linting tool references.
- The commit guidelines do not reference Conventional Commits or do not include examples.
- The tone contains motivational, emotional, or community-building language.

Non-compliance **must** be resolved before release.