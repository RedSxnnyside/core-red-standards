# Changelog Standard

This document defines the standard template and rules for the CHANGELOG file required in every Core Red repository. Projects **must** include a `CHANGELOG.md` at the repository root that conforms to this standard.

The CHANGELOG is the authoritative record of what changed, when, and in which version. It is a controlled artifact, not a narrative. Every entry exists to document a discrete, verifiable change. The CHANGELOG is written for humans who need to determine whether to upgrade, what broke, and what was fixed.

---

## Format

The CHANGELOG **must** follow the structure defined in this standard. It is based on the [Keep a Changelog](https://keepachangelog.com/) convention, with Core Red–specific constraints.

---

## File Structure

The CHANGELOG **must** begin with the document title, followed by a brief description, followed by release entries in reverse chronological order (newest first).

```markdown
# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [vX.Y.Z] - YYYY-MM-DD

### Added
### Changed
### Deprecated
### Removed
### Fixed
### Security
```

---

## Section Requirements

### CL-01 — Document Title

The first line of the CHANGELOG **must** be `# Changelog`.

### CL-02 — Preamble

A preamble **must** appear immediately after the title. The preamble **must** state:

- That all notable changes are documented in the file.
- That the format is based on Keep a Changelog.
- That the project adheres to Semantic Versioning.

This preamble establishes the contract. It is not decorative.

### CL-03 — Release Heading Format

Each release **must** use an H2 heading with the following format:

```markdown
## [vX.Y.Z] - YYYY-MM-DD
```

- The version **must** follow semantic versioning with the `v` prefix.
- The date **must** use ISO 8601 format (`YYYY-MM-DD`).
- The version and date **must** be separated by ` - ` (space-hyphen-space).

### CL-04 — Unreleased Section

An `## [Unreleased]` section **may** appear at the top of the CHANGELOG to track changes not yet included in a release. When present, it **must** appear directly below the preamble, above all versioned entries. This section **must** be converted to a versioned entry at the time of release.

### CL-05 — Reverse Chronological Order

Release entries **must** be ordered from newest to oldest. The most recent release **must** appear directly below the preamble (or below the Unreleased section, if present).

---

## Change Categories

Each release entry **must** use only the following H3 categories. Categories with no entries for that release **must** be omitted entirely.

| Category | Usage |
|---|---|
| `Added` | New features or capabilities. |
| `Changed` | Modifications to existing behavior. |
| `Deprecated` | Features marked for future removal. |
| `Removed` | Features or capabilities that have been removed. |
| `Fixed` | Bug fixes and corrections. |
| `Security` | Changes that address security vulnerabilities. |

### CL-06 — No Custom Categories

Categories not listed above are not permitted. All changes **must** fit within the defined categories. If a change does not fit, it belongs in `Changed`.

### CL-07 — Category Order

When multiple categories appear in a single release entry, they **must** appear in the order listed in the table above: Added, Changed, Deprecated, Removed, Fixed, Security.

---

## Entry Rules

### CL-08 — One Change per Entry

Each list item **must** describe a single change. Combining multiple changes into a single entry is prohibited.

| Correct | Incorrect |
|---|---|
| Add input validation for configuration parser. | Add input validation and fix error handling for config parser. |
| Fix error handling for configuration parser. | |

### CL-09 — Imperative Mood

Entries **must** use imperative mood. This matches the Git commit convention and the project's commit guidelines.

| Correct | Incorrect |
|---|---|
| Add input validation for configuration parser. | Added input validation for configuration parser. |
| Fix memory leak in connection pool. | Fixed a memory leak in the connection pool. |
| Remove deprecated v1 API routes. | Removing deprecated v1 API routes. |

### CL-10 — Specific and Factual

Entries **must** describe what changed with sufficient specificity for a reader to understand the impact without reading the source code. Vague entries are non-compliant.

| Correct | Incorrect |
|---|---|
| Add rate limiting to the authentication endpoint. | Improve security. |
| Remove deprecated `v1` API routes. | Clean up old code. |
| Fix incorrect timezone offset in scheduled task execution. | Fix bug. |
| Change default connection timeout from 30s to 60s. | Update configuration defaults. |

### CL-11 — No Emotional or Subjective Language

Entries **must not** contain opinions, gratitude, apologies, or subjective assessments. The CHANGELOG documents facts.

| Correct | Incorrect |
|---|---|
| Fix crash when input exceeds 10 MB. | Finally fix the annoying crash. |
| Add dark mode support. | Add the much-requested dark mode. |

### CL-12 — Issue References

Entries **should** include a reference to the associated issue or pull request when applicable. The reference **must** be parenthesized at the end of the entry.

```markdown
- Fix null pointer exception in query builder. (#142)
- Add support for TOML configuration files. (#88)
```

### CL-13 — No Duplicate Entries

A single change **must not** appear in multiple categories within the same release. Choose the most accurate category.

---

## Canonical Template

The following template contains placeholders only. No project-specific entries are permitted in the standard. Projects **must** populate this template with their own entries at the time of release.

```markdown
# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

### Added

- <DESCRIPTION_OF_ADDED_FEATURE_OR_CAPABILITY>.

## [v<MAJOR>.<MINOR>.<PATCH>] - <YYYY-MM-DD>

### Added

- <DESCRIPTION_OF_ADDED_FEATURE_OR_CAPABILITY>.
- <DESCRIPTION_OF_ADDED_FEATURE_OR_CAPABILITY>.

### Changed

- <DESCRIPTION_OF_CHANGED_BEHAVIOR>.

### Deprecated

- <DESCRIPTION_OF_DEPRECATED_FEATURE>.

### Removed

- <DESCRIPTION_OF_REMOVED_FEATURE>.

### Fixed

- <DESCRIPTION_OF_BUG_FIX>. (#<ISSUE_NUMBER>)
- <DESCRIPTION_OF_BUG_FIX>.

### Security

- <DESCRIPTION_OF_SECURITY_FIX>.

## [v<MAJOR>.<MINOR>.<PATCH>] - <YYYY-MM-DD>

### Added

- <DESCRIPTION_OF_ADDED_FEATURE_OR_CAPABILITY>.
```

---

## Placeholder Fields

| Placeholder | Description |
|---|---|
| `<MAJOR>` | The major version number. |
| `<MINOR>` | The minor version number. |
| `<PATCH>` | The patch version number. |
| `<YYYY-MM-DD>` | The release date in ISO 8601 format. |
| `<DESCRIPTION_OF_ADDED_FEATURE_OR_CAPABILITY>` | A single imperative-mood sentence describing an addition. |
| `<DESCRIPTION_OF_CHANGED_BEHAVIOR>` | A single imperative-mood sentence describing a behavioral change. |
| `<DESCRIPTION_OF_DEPRECATED_FEATURE>` | A single imperative-mood sentence describing a deprecation. |
| `<DESCRIPTION_OF_REMOVED_FEATURE>` | A single imperative-mood sentence describing a removal. |
| `<DESCRIPTION_OF_BUG_FIX>` | A single imperative-mood sentence describing a fix. |
| `<DESCRIPTION_OF_SECURITY_FIX>` | A single imperative-mood sentence describing a security change. |
| `<ISSUE_NUMBER>` | The issue or pull request number associated with the change. |

---

## Compliance

A CHANGELOG file is non-compliant if any of the following conditions are true:

- The file is absent from the repository root.
- The preamble is missing or does not reference Keep a Changelog and Semantic Versioning.
- Release entries do not follow the required heading format.
- Entries use past tense instead of imperative mood.
- Entries are vague, combine multiple changes, or contain subjective language.
- Custom categories are used.
- Categories within a release are not in the defined order.
- Release entries are not in reverse chronological order.
- Dates do not use ISO 8601 format.

Non-compliance **must** be resolved before release.
