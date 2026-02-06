# File Manifest Standard

This document defines the standard template for the FILE_MANIFEST file in Core Red repositories. The FILE_MANIFEST file is **optional**. It provides a comprehensive, annotated listing of every significant file and directory in the repository, serving as a navigational index for the codebase.

The FILE_MANIFEST differs from the ARCHITECTURE directory tree in scope and purpose. The ARCHITECTURE directory tree documents structural relationships and component boundaries. The FILE_MANIFEST documents individual file purpose, ownership, and status. Where the architecture tree answers "How is this organized?", the file manifest answers "What is this file, and why is it here?"

---

## When This Document Applies

A project **should** include a `FILE_MANIFEST.md` file when any of the following conditions are true:

- The repository contains more than 50 files.
- The repository contains files whose purpose is not obvious from their name or location (e.g., configuration files with non-standard names, generated files, compatibility shims).
- Multiple teams or contributors work in the repository and need a shared reference for file ownership.
- The project undergoes periodic audits that require verifying every file has a documented purpose.

A project **may** omit `FILE_MANIFEST.md` when the repository is small enough (fewer than 20 files) that the ARCHITECTURE directory tree or README file listing is sufficient.

---

## Template Structure

The FILE_MANIFEST file **must** contain the following sections, in this order.

1. Overview
2. Conventions
3. Root Files
4. Directory Listings (one subsection per top-level directory)
5. Generated Files (conditional: omit only if no generated files exist)
6. Deprecated Files (conditional: omit only if no deprecated files exist)

---

## Section Requirements

### Overview

A one-paragraph statement of the manifest's scope. The overview **must** state:

- The total number of tracked files and directories.
- The date the manifest was last verified against the actual repository contents.
- Who is responsible for maintaining the manifest.

The verification date is critical. A file manifest that does not state when it was last verified cannot be trusted.

Format:

```markdown
## Overview

This manifest documents <FILE_COUNT> files and <DIRECTORY_COUNT> directories in the <PROJECT_NAME> repository. Last verified against the repository on <VERIFICATION_DATE> by <VERIFIER>.
```

### Conventions

A brief section documenting the notation used in the manifest. This **must** include:

- The meaning of any status indicators used (e.g., what "generated", "deprecated", "locked" mean).
- How ownership is denoted.
- Any file categories used and their definitions.

This section ensures the manifest is self-documenting. Readers do not need to consult an external reference to interpret the manifest.

### Root Files

A table listing every file in the repository root. Each entry **must** include:

| File | Category | Description | Owner |
|---|---|---|---|
| `<FILE_NAME>` | `<CATEGORY>` | `<FILE_DESCRIPTION>` | `<OWNER>` |

Column definitions:

- **File**: The file name.
- **Category**: The file's functional category (see Categories below).
- **Description**: One sentence describing the file's purpose.
- **Owner**: The team, role, or individual responsible for the file.

### Directory Listings

Each top-level directory **must** have its own H3 subsection. Within each subsection, a table lists all files in that directory (including subdirectories). Subdirectories **must** be listed before files within them.

Format:

```markdown
### <DIRECTORY_NAME>/

<DIRECTORY_DESCRIPTION>

| Path | Category | Description | Owner |
|---|---|---|---|
| `<RELATIVE_PATH>` | `<CATEGORY>` | `<FILE_DESCRIPTION>` | `<OWNER>` |
| `<RELATIVE_PATH>` | `<CATEGORY>` | `<FILE_DESCRIPTION>` | `<OWNER>` |
```

The directory description is one to two sentences explaining the directory's purpose and what types of files it contains.

For deeply nested directories (more than 3 levels), subdirectories **may** be grouped with a path prefix rather than receiving their own subsection.

### Generated Files

A table listing all files that are produced by build tools, code generators, or automated processes rather than authored by hand. Generated files **must** be tracked in the manifest so that contributors do not manually edit them.

| File | Generator | Regeneration Command | Notes |
|---|---|---|---|
| `<GENERATED_FILE>` | `<GENERATOR_NAME>` | `<REGENERATION_COMMAND>` | `<NOTES>` |

Column definitions:

- **File**: Path to the generated file.
- **Generator**: The tool, script, or process that produces the file.
- **Regeneration Command**: The exact command to regenerate the file.
- **Notes**: Any additional context (e.g., "Do not edit manually", "Committed for CI compatibility").

This section **may** be omitted if the repository contains no generated files.

### Deprecated Files

A table listing files that still exist in the repository but are scheduled for removal or are no longer actively used.

| File | Deprecated Since | Removal Target | Replacement | Reason |
|---|---|---|---|---|
| `<DEPRECATED_FILE>` | `<DEPRECATION_DATE>` | `<REMOVAL_TARGET>` | `<REPLACEMENT>` | `<DEPRECATION_REASON>` |

Column definitions:

- **File**: Path to the deprecated file.
- **Deprecated Since**: ISO 8601 date when the file was deprecated.
- **Removal Target**: The version or date by which the file will be removed.
- **Replacement**: The file or process that replaces it, or "None" if no replacement exists.
- **Reason**: Why the file was deprecated.

This section **may** be omitted if no deprecated files exist.

---

## Categories

The following categories **must** be used consistently across all manifest entries. Projects **may** define additional categories in the Conventions section if needed.

| Category | Definition |
|---|---|
| `config` | Configuration files (package.json, tsconfig.json, .env.example). |
| `source` | Application source code. |
| `test` | Test files and test utilities. |
| `docs` | Documentation files (README, CHANGELOG, CONTRIBUTING, etc.). |
| `build` | Build scripts, Makefiles, CI/CD pipeline definitions. |
| `asset` | Static assets (images, fonts, templates, fixtures). |
| `generated` | Files produced by automated processes. Must also appear in Generated Files section. |
| `meta` | Repository metadata (.gitignore, .editorconfig, LICENSE). |
| `script` | Utility scripts not part of the application source (setup scripts, migration scripts). |

---

## Canonical Template

```markdown
# File Manifest

## Overview

This manifest documents <FILE_COUNT> files and <DIRECTORY_COUNT> directories in the <PROJECT_NAME> repository. Last verified against the repository on <VERIFICATION_DATE> by <VERIFIER>.

## Conventions

- **Category**: Each file is assigned a functional category as defined in the project standards.
- **Owner**: The team or individual responsible for maintaining the file.
- **Status Indicators**:
  - No indicator: Active, hand-authored file.
  - `generated`: Produced by an automated process. Do not edit manually.
  - `deprecated`: Scheduled for removal. See Deprecated Files section.
  - `locked`: Changes require approval from the file owner.

## Root Files

| File | Category | Description | Owner |
|---|---|---|---|
| <FILE_NAME> | <CATEGORY> | <FILE_DESCRIPTION> | <OWNER> |
| <FILE_NAME> | <CATEGORY> | <FILE_DESCRIPTION> | <OWNER> |
| <FILE_NAME> | <CATEGORY> | <FILE_DESCRIPTION> | <OWNER> |
| <FILE_NAME> | <CATEGORY> | <FILE_DESCRIPTION> | <OWNER> |

## Directory Listings

### <DIRECTORY_NAME>/

<DIRECTORY_DESCRIPTION>

| Path | Category | Description | Owner |
|---|---|---|---|
| <RELATIVE_PATH> | <CATEGORY> | <FILE_DESCRIPTION> | <OWNER> |
| <RELATIVE_PATH> | <CATEGORY> | <FILE_DESCRIPTION> | <OWNER> |

### <DIRECTORY_NAME>/

<DIRECTORY_DESCRIPTION>

| Path | Category | Description | Owner |
|---|---|---|---|
| <RELATIVE_PATH> | <CATEGORY> | <FILE_DESCRIPTION> | <OWNER> |
| <RELATIVE_PATH> | <CATEGORY> | <FILE_DESCRIPTION> | <OWNER> |

## Generated Files

| File | Generator | Regeneration Command | Notes |
|---|---|---|---|
| <GENERATED_FILE> | <GENERATOR_NAME> | `<REGENERATION_COMMAND>` | <NOTES> |

## Deprecated Files

| File | Deprecated Since | Removal Target | Replacement | Reason |
|---|---|---|---|---|
| <DEPRECATED_FILE> | <DEPRECATION_DATE> | <REMOVAL_TARGET> | <REPLACEMENT> | <DEPRECATION_REASON> |
```

---

## Placeholder Fields

| Placeholder | Description |
|---|---|
| `<FILE_COUNT>` | Total number of tracked files in the repository. |
| `<DIRECTORY_COUNT>` | Total number of tracked directories in the repository. |
| `<PROJECT_NAME>` | The official name of the project. Must match the README. |
| `<VERIFICATION_DATE>` | ISO 8601 date when the manifest was last verified against the repository. |
| `<VERIFIER>` | The person or team who performed the verification. |
| `<FILE_NAME>` | Name of a file in the repository root. |
| `<CATEGORY>` | Functional category of the file (config, source, test, docs, build, asset, generated, meta, script). |
| `<FILE_DESCRIPTION>` | One-sentence description of the file's purpose. |
| `<OWNER>` | Team, role, or individual responsible for the file. |
| `<DIRECTORY_NAME>` | Name of a top-level directory. |
| `<DIRECTORY_DESCRIPTION>` | One to two sentences describing the directory's purpose. |
| `<RELATIVE_PATH>` | Relative path to a file within a directory. |
| `<GENERATED_FILE>` | Path to a generated file. |
| `<GENERATOR_NAME>` | Tool or process that produces the generated file. |
| `<REGENERATION_COMMAND>` | Exact command to regenerate the file. |
| `<NOTES>` | Additional context for the generated file. |
| `<DEPRECATED_FILE>` | Path to a deprecated file. |
| `<DEPRECATION_DATE>` | ISO 8601 date when the file was deprecated. |
| `<REMOVAL_TARGET>` | Version or date by which the deprecated file will be removed. |
| `<REPLACEMENT>` | File or process that replaces the deprecated file, or "None." |
| `<DEPRECATION_REASON>` | Why the file was deprecated. |

---

## Maintenance

The file manifest is a living document. It **must** be updated whenever:

- A file is added to or removed from the repository.
- A file is moved or renamed.
- A file's purpose or ownership changes.
- A file is deprecated or un-deprecated.

The verification date in the Overview section **must** be updated each time the manifest is verified against the actual repository contents. Verification **should** occur at least once per release cycle.

Automated tooling **may** be used to detect drift between the manifest and the repository. However, automated tools **must not** generate manifest entries without human review of the descriptions and ownership assignments.

---

## Compliance

A FILE_MANIFEST file is non-compliant if any of the following conditions are true:

- The overview does not state the verification date.
- The overview does not state the verifier.
- A file exists in the repository but does not appear in the manifest.
- A file appears in the manifest but does not exist in the repository.
- File descriptions are missing or are generic (e.g., "configuration file" without specifying what it configures).
- Categories are used inconsistently or are undefined.
- Generated files are not identified as generated.
- Deprecated files are not listed in the Deprecated Files section.
- The tone contains marketing, motivational, or emotional language.
- Placeholder fields have not been replaced with project-specific values.

Non-compliance **must** be resolved before release.