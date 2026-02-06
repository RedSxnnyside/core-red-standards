# Quickstart Standard

This document defines the standard template for the QUICKSTART file in Core Red repositories. The QUICKSTART file is **optional**. It provides a minimal, step-by-step path from zero to a working instance of the project, designed for users who want to get running as fast as possible without reading the full README.

The QUICKSTART is not a replacement for the README. It deliberately omits configuration options, architectural context, and advanced usage. It documents exactly one path: the shortest complete sequence of commands and actions required to install, configure, and verify the project.

---

## When This Document Applies

A project **should** include a `QUICKSTART.md` file when any of the following conditions are true:

- The README Installation and Usage sections together exceed 40 lines.
- The project requires more than 3 setup steps before first use.
- The project serves users who may not need to understand the full system to use it (e.g., end users of a CLI tool, consumers of a library).
- The project has multiple installation methods, and the QUICKSTART can document a single recommended path.

A project **may** omit `QUICKSTART.md` when the README Installation section is concise enough to serve as a quickstart on its own (i.e., 3 or fewer steps with no conditional branching).

---

## Template Structure

The QUICKSTART file **must** contain the following sections, in this order.

1. Title
2. Prerequisites
3. Install
4. Configure (conditional: omit only if the project requires zero configuration before first use)
5. Run
6. Verify
7. Next Steps

---

## Section Requirements

### Title

The H1 heading **must** be "Quickstart" followed by the project name. No subtitle is required.

Format: `# Quickstart: <PROJECT_NAME>`

### Prerequisites

A complete list of everything the user must have installed or configured before beginning the quickstart. Each prerequisite **must** include:

- The name of the required tool, runtime, or system.
- The minimum version required.
- A verification command the user can run to confirm the prerequisite is met.

Format:

```markdown
## Prerequisites

| Prerequisite | Minimum Version | Verify |
|---|---|---|
| <PREREQUISITE_NAME> | <MINIMUM_VERSION> | `<VERIFY_COMMAND>` |
```

The prerequisites list **must** be exhaustive. If following the quickstart fails because of a missing prerequisite not listed here, the document is non-compliant.

### Install

The exact commands required to install the project. This section **must** document one path only. If the project supports multiple installation methods, the QUICKSTART documents the recommended method. Alternative methods are documented in the README.

Each step **must** be numbered. Each step **must** contain a fenced code block with the exact command to run. Brief explanatory text (one sentence maximum) **may** precede each code block.

Format:

```markdown
## Install

1. <INSTALL_STEP_DESCRIPTION>

\`\`\`<LANGUAGE>
<INSTALL_COMMAND>
\`\`\`

2. <INSTALL_STEP_DESCRIPTION>

\`\`\`<LANGUAGE>
<INSTALL_COMMAND>
\`\`\`
```

The language identifier for the code block **must** match the shell or environment (e.g., `bash`, `powershell`, `sh`). If a command is platform-specific, the step **must** state the platform.

### Configure

The minimum configuration required before the project can be run. This section **must not** document all configuration options. It documents only the values that must be set for the project to start.

Each configuration step **must** include:

- What file or environment variable to set.
- What value to set it to (or a placeholder with instructions for obtaining the value).
- The exact command or edit required.

Format:

```markdown
## Configure

1. <CONFIGURE_STEP_DESCRIPTION>

\`\`\`<LANGUAGE>
<CONFIGURE_COMMAND>
\`\`\`
```

This section **may** be omitted if the project requires zero configuration to run after installation. "Zero configuration" means the project ships with defaults sufficient for first use.

### Run

The exact command to start the project. This section **must** contain:

- A single fenced code block with the command to run.
- A brief description (one to two sentences) of what the user should expect to see when the command succeeds.

Format:

```markdown
## Run

Start the project:

\`\`\`<LANGUAGE>
<RUN_COMMAND>
\`\`\`

<EXPECTED_OUTPUT_DESCRIPTION>
```

If the project has a startup delay (e.g., a server that needs time to bind to a port), the expected behavior during startup **must** be documented.

### Verify

How the user confirms the project is working correctly. The verification step **must** be concrete and observable. It **must** produce output the user can compare to an expected value.

This section **must** include:

- The verification command.
- The expected output or behavior.

Format:

```markdown
## Verify

Run the following command to confirm the project is working:

\`\`\`<LANGUAGE>
<VERIFY_COMMAND>
\`\`\`

Expected output:

\`\`\`text
<EXPECTED_OUTPUT>
\`\`\`
```

The expected output **must** be exact. If the output varies (e.g., includes timestamps or dynamic values), the document **must** describe which parts are fixed and which vary.

### Next Steps

A bulleted list of links directing the user to the next relevant resources after completing the quickstart. Each link **must** include a one-sentence description of what the user will find there.

The Next Steps section **must** include at least:

- A link to the full README for comprehensive documentation.
- A link to the CONTRIBUTING file if the user might want to contribute.

Format:

```markdown
## Next Steps

- [<LINK_TEXT>](<LINK_TARGET>) — <LINK_DESCRIPTION>
- [<LINK_TEXT>](<LINK_TARGET>) — <LINK_DESCRIPTION>
- [<LINK_TEXT>](<LINK_TARGET>) — <LINK_DESCRIPTION>
```

---

## Canonical Template

```markdown
# Quickstart: <PROJECT_NAME>

## Prerequisites

| Prerequisite | Minimum Version | Verify |
|---|---|---|
| <PREREQUISITE_NAME> | <MINIMUM_VERSION> | `<VERIFY_COMMAND>` |
| <PREREQUISITE_NAME> | <MINIMUM_VERSION> | `<VERIFY_COMMAND>` |

## Install

1. <INSTALL_STEP_DESCRIPTION>

\`\`\`<LANGUAGE>
<INSTALL_COMMAND>
\`\`\`

2. <INSTALL_STEP_DESCRIPTION>

\`\`\`<LANGUAGE>
<INSTALL_COMMAND>
\`\`\`

## Configure

1. <CONFIGURE_STEP_DESCRIPTION>

\`\`\`<LANGUAGE>
<CONFIGURE_COMMAND>
\`\`\`

2. <CONFIGURE_STEP_DESCRIPTION>

\`\`\`<LANGUAGE>
<CONFIGURE_COMMAND>
\`\`\`

## Run

Start the project:

\`\`\`<LANGUAGE>
<RUN_COMMAND>
\`\`\`

<EXPECTED_OUTPUT_DESCRIPTION>

## Verify

Run the following command to confirm the project is working:

\`\`\`<LANGUAGE>
<VERIFY_COMMAND>
\`\`\`

Expected output:

\`\`\`text
<EXPECTED_OUTPUT>
\`\`\`

## Next Steps

- [README](README.md) — Full project documentation including configuration, usage, and architecture.
- [CONTRIBUTING](<CONTRIBUTING_PATH>) — How to contribute to the project.
- [<LINK_TEXT>](<LINK_TARGET>) — <LINK_DESCRIPTION>
```

---

## Placeholder Fields

| Placeholder | Description |
|---|---|
| `<PROJECT_NAME>` | The official name of the project. Must match the README. |
| `<PREREQUISITE_NAME>` | Name of a required tool, runtime, or system. |
| `<MINIMUM_VERSION>` | Minimum required version of the prerequisite. |
| `<VERIFY_COMMAND>` | Command to verify the prerequisite is installed. |
| `<INSTALL_STEP_DESCRIPTION>` | Brief description of what the install step does. |
| `<LANGUAGE>` | Language identifier for the code block (bash, powershell, sh). |
| `<INSTALL_COMMAND>` | Exact command to run for installation. |
| `<CONFIGURE_STEP_DESCRIPTION>` | Brief description of the configuration step. |
| `<CONFIGURE_COMMAND>` | Exact command or edit for configuration. |
| `<RUN_COMMAND>` | Command to start the project. |
| `<EXPECTED_OUTPUT_DESCRIPTION>` | What the user should expect to see on successful startup. |
| `<VERIFY_COMMAND>` | Command to verify the project is working. |
| `<EXPECTED_OUTPUT>` | Exact expected output from the verification command. |
| `<LINK_TEXT>` | Display text for a Next Steps link. |
| `<LINK_TARGET>` | Relative path or URL for the link target. |
| `<LINK_DESCRIPTION>` | One-sentence description of what the linked resource contains. |
| `<CONTRIBUTING_PATH>` | Relative path to the CONTRIBUTING file. |

---

## Compliance

A QUICKSTART file is non-compliant if any of the following conditions are true:

- The prerequisites list is incomplete (following the quickstart fails due to a missing prerequisite).
- The install section documents more than one installation method.
- Commands are described in prose rather than provided in fenced code blocks.
- The run section does not describe expected startup behavior.
- The verify section does not provide expected output for comparison.
- The next steps section does not link to the full README.
- The document includes configuration options, architectural context, or advanced usage.
- The tone contains marketing, motivational, or emotional language.
- Placeholder fields have not been replaced with project-specific values.

Non-compliance **must** be resolved before release.