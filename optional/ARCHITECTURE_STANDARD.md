# Architecture Standard

This document defines the standard template for the ARCHITECTURE file in Core Red repositories. The ARCHITECTURE file is **optional**. It is required only when the project's architectural complexity exceeds the scope of the README Architecture section, as defined in the [PUBLIC_README_STANDARD.md](../mandatory/PUBLIC_README_STANDARD.md).

The ARCHITECTURE file provides a comprehensive, text-first description of the project's internal structure. It documents how components are organized, how they communicate, and what responsibilities each component owns. Where the README Architecture section provides a snapshot, the ARCHITECTURE file provides the full map.

---

## When This Document Applies

A project **must** include an `ARCHITECTURE.md` file when any of the following conditions are true:

- The directory tree exceeds 30 lines.
- The system has more than 5 distinct components or services.
- The architecture requires data flow descriptions, inter-component communication details, or protocol definitions.
- The project includes multiple runtimes, build targets, or deployment artifacts.

A project **may** omit `ARCHITECTURE.md` when the README Architecture section (inline mode) is sufficient to communicate the full structure. See the README standard's Architecture Handling section for the threshold criteria.

When `ARCHITECTURE.md` is present, the README Architecture section **must** still exist. It provides a summary paragraph and a link to this file. It does not become empty.

---

## Template Structure

The ARCHITECTURE file **must** contain the following sections, in this order. Sections marked as conditional **may** be omitted only when the stated condition applies.

1. Overview
2. Directory Structure
3. Component Descriptions
4. Stack
5. Data Flow (conditional: omit only if no inter-component communication exists)
6. Build Targets (conditional: omit only if a single build artifact exists)
7. Design Decisions (conditional: omit only if no significant architectural decisions need documentation)

---

## Section Requirements

### Overview

A one-to-three paragraph summary of the project's architecture. The overview **must** state:

- What the system is composed of at the highest level.
- How the major components relate to each other.
- What the primary execution path is (e.g., "User input enters through the CLI, is processed by the core engine, and output is rendered by the UI layer").

The overview is a narrative orientation. It provides the reader with a mental model before they encounter structural details.

### Directory Structure

A complete directory tree in a fenced code block. Every directory and significant file **must** include an inline comment describing its purpose.

The tree **must** reflect the actual repository structure. Out-of-date trees are a compliance failure.

Format:

```text
<PROJECT_DIRECTORY>/
├── <DIRECTORY>/               # <DESCRIPTION>
│   └── <SUBDIRECTORY>/
│       ├── <FILE>             # <DESCRIPTION>
│       ├── <FILE>             # <DESCRIPTION>
│       └── <FILE>             # <DESCRIPTION>
│
├── <DIRECTORY>/               # <DESCRIPTION>
│   ├── <SUBDIRECTORY>/        # <DESCRIPTION>
│   ├── <SUBDIRECTORY>/        # <DESCRIPTION>
│   └── <FILE>                 # <DESCRIPTION>
│
└── <DIRECTORY>/               # <DESCRIPTION>
```

Files that are boilerplate (e.g., `.gitignore`, `LICENSE`) **may** be omitted from the tree unless they have project-specific significance.

### Component Descriptions

Each major component of the system **must** be documented in its own H3 subsection. A "component" is a directory or module that owns a distinct area of responsibility.

Each component subsection **must** include:

- **Purpose**: One to two sentences defining what the component does.
- **Responsibilities**: A bulleted list of the component's specific responsibilities.
- **Key Files**: A bulleted list of the most important files within the component, each with a one-sentence description.
- **Dependencies**: Which other components this component depends on, and the nature of the dependency (e.g., "calls the API of", "reads configuration from", "receives events from").

Format:

```markdown
### <COMPONENT_NAME>

**Purpose**: <COMPONENT_PURPOSE>

**Responsibilities**:

- <RESPONSIBILITY>
- <RESPONSIBILITY>
- <RESPONSIBILITY>

**Key Files**:

- `<FILE_PATH>` — <FILE_DESCRIPTION>
- `<FILE_PATH>` — <FILE_DESCRIPTION>

**Dependencies**: <DEPENDENCY_DESCRIPTION>
```

### Stack

A table listing the technology used for each architectural component. This is the same Stack table defined in the README standard, but it **may** be more detailed in the ARCHITECTURE file.

| Component | Technology | Purpose |
|---|---|---|
| `<COMPONENT_NAME>` | `<TECHNOLOGY_NAME>` | `<PURPOSE>` |

The Purpose column is optional in the README Stack table but **should** be included in the ARCHITECTURE file for additional clarity.

### Data Flow

This section documents how data moves through the system. It **must** describe:

- The entry points where data enters the system (e.g., CLI arguments, HTTP requests, file reads).
- The transformations applied to the data at each stage.
- The exit points where data leaves the system (e.g., stdout, file writes, network responses).

Present the data flow as a numbered sequence. Each step **must** identify the component responsible for the operation.

Format:

```markdown
1. <ENTRY_POINT_DESCRIPTION> → `<COMPONENT>`
2. `<COMPONENT>` processes <TRANSFORMATION_DESCRIPTION> → `<COMPONENT>`
3. `<COMPONENT>` renders <OUTPUT_DESCRIPTION> → <EXIT_POINT>
```

If the system has multiple distinct data flows (e.g., CLI path vs. desktop path), each **must** be documented in its own H3 subsection.

This section **may** be omitted if the project has no inter-component communication — that is, if the entire system is a single module with a single execution path.

### Build Targets

This section documents all distinct build outputs. Each build target **must** have its own H3 subsection containing:

- **Target**: The name or identifier of the build target.
- **Output**: What the build produces (e.g., a binary, a bundle, a container image).
- **Command**: The command to produce the target.
- **Notes**: Any additional context (e.g., platform requirements, environment variables).

This section **may** be omitted if the project produces a single build artifact documented in the README Installation section.

### Design Decisions

This section documents significant architectural decisions and their rationale. Each decision **must** be presented as an H3 subsection with a descriptive title.

Each decision entry **must** include:

- **Decision**: A one-sentence statement of what was decided.
- **Rationale**: Why this decision was made, including alternatives that were considered and rejected.
- **Consequences**: The trade-offs or implications of the decision.

This section is valuable for onboarding new contributors and preventing the re-litigation of settled decisions. It **may** be omitted if no significant architectural decisions need documentation.

---

## Canonical Template

```markdown
# Architecture

## Overview

<ARCHITECTURE_OVERVIEW>

## Directory Structure

\`\`\`text
<PROJECT_DIRECTORY>/
├── <DIRECTORY>/               # <DESCRIPTION>
│   └── <SUBDIRECTORY>/
│       ├── <FILE>             # <DESCRIPTION>
│       └── <FILE>             # <DESCRIPTION>
│
├── <DIRECTORY>/               # <DESCRIPTION>
│   ├── <SUBDIRECTORY>/        # <DESCRIPTION>
│   └── <SUBDIRECTORY>/        # <DESCRIPTION>
│
└── <DIRECTORY>/               # <DESCRIPTION>
\`\`\`

## Component Descriptions

### <COMPONENT_NAME>

**Purpose**: <COMPONENT_PURPOSE>

**Responsibilities**:

- <RESPONSIBILITY>
- <RESPONSIBILITY>

**Key Files**:

- `<FILE_PATH>` — <FILE_DESCRIPTION>
- `<FILE_PATH>` — <FILE_DESCRIPTION>

**Dependencies**: <DEPENDENCY_DESCRIPTION>

### <COMPONENT_NAME>

**Purpose**: <COMPONENT_PURPOSE>

**Responsibilities**:

- <RESPONSIBILITY>
- <RESPONSIBILITY>

**Key Files**:

- `<FILE_PATH>` — <FILE_DESCRIPTION>
- `<FILE_PATH>` — <FILE_DESCRIPTION>

**Dependencies**: <DEPENDENCY_DESCRIPTION>

## Stack

| Component | Technology | Purpose |
|---|---|---|
| <COMPONENT_NAME> | <TECHNOLOGY_NAME> | <PURPOSE> |
| <COMPONENT_NAME> | <TECHNOLOGY_NAME> | <PURPOSE> |
| <COMPONENT_NAME> | <TECHNOLOGY_NAME> | <PURPOSE> |

## Data Flow

### <DATA_FLOW_NAME>

1. <ENTRY_POINT_DESCRIPTION> → `<COMPONENT>`
2. `<COMPONENT>` processes <TRANSFORMATION_DESCRIPTION> → `<COMPONENT>`
3. `<COMPONENT>` renders <OUTPUT_DESCRIPTION> → <EXIT_POINT>

## Build Targets

### <BUILD_TARGET_NAME>

- **Target**: <TARGET_NAME>
- **Output**: <OUTPUT_DESCRIPTION>
- **Command**: `<BUILD_COMMAND>`
- **Notes**: <ADDITIONAL_CONTEXT>

## Design Decisions

### <DECISION_TITLE>

- **Decision**: <DECISION_STATEMENT>
- **Rationale**: <RATIONALE>
- **Consequences**: <CONSEQUENCES>
```

---

## Placeholder Fields

| Placeholder | Description |
|---|---|
| `<ARCHITECTURE_OVERVIEW>` | One to three paragraphs summarizing the system's architecture. |
| `<PROJECT_DIRECTORY>` | The root directory name of the project. |
| `<DIRECTORY>` | A directory in the project tree. |
| `<SUBDIRECTORY>` | A subdirectory within a directory. |
| `<FILE>` | A file within a directory. |
| `<DESCRIPTION>` | Inline comment describing the purpose of a directory or file. |
| `<COMPONENT_NAME>` | The name of an architectural component. |
| `<COMPONENT_PURPOSE>` | One to two sentences defining the component's purpose. |
| `<RESPONSIBILITY>` | A specific responsibility owned by the component. |
| `<FILE_PATH>` | Relative path to a key file within the component. |
| `<FILE_DESCRIPTION>` | One-sentence description of the file's purpose. |
| `<DEPENDENCY_DESCRIPTION>` | Description of inter-component dependencies. |
| `<TECHNOLOGY_NAME>` | The technology used for the component. |
| `<PURPOSE>` | The purpose of using the technology for the component. |
| `<DATA_FLOW_NAME>` | Descriptive name for a distinct data flow path. |
| `<ENTRY_POINT_DESCRIPTION>` | How data enters the system at this step. |
| `<TRANSFORMATION_DESCRIPTION>` | What transformation is applied to the data. |
| `<OUTPUT_DESCRIPTION>` | What the system produces as output. |
| `<EXIT_POINT>` | Where data leaves the system (stdout, file, network). |
| `<BUILD_TARGET_NAME>` | Descriptive heading for a build target. |
| `<TARGET_NAME>` | The identifier of the build target. |
| `<BUILD_COMMAND>` | The command to produce the build artifact. |
| `<ADDITIONAL_CONTEXT>` | Platform requirements, environment variables, or constraints. |
| `<DECISION_TITLE>` | Descriptive title for an architectural decision. |
| `<DECISION_STATEMENT>` | One-sentence statement of the decision. |
| `<RATIONALE>` | Why the decision was made, including rejected alternatives. |
| `<CONSEQUENCES>` | Trade-offs or implications of the decision. |

---

## Compliance

An ARCHITECTURE file is non-compliant if any of the following conditions are true:

- The file is required (per the threshold criteria) but absent.
- The README Architecture section does not link to `ARCHITECTURE.md` when the file exists.
- The overview section is missing or does not provide a navigable mental model.
- The directory tree is absent or out of date.
- Components are listed without purpose, responsibilities, or key file descriptions.
- The stack table is absent.
- Data flow is not documented when inter-component communication exists.
- The tone contains marketing, motivational, or emotional language.
- Placeholder fields have not been replaced with project-specific values.

Non-compliance **must** be resolved before release.