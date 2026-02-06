# Project Configuration File Standard

This standard defines how root-level project configuration files are structured and documented across all Core Red projects.

---

## Scope

This standard applies exclusively to root-level project configuration files that define project identity and metadata. These include:

- `package.json` (Node.js)
- `pubspec.yaml` (Dart / Flutter)
- `Cargo.toml` (Rust)
- `pyproject.toml` (Python)
- Equivalent root-level project manifests in other ecosystems

This standard does **not** apply to:

- Tool-specific configuration files (e.g., `tsconfig.json`, `tailwind.config.js`, `.eslintrc`, bundler configurations)
- Framework-specific settings files
- Environment files (governed by [ENVEXAMPLE_STANDARD.md](ENVEXAMPLE_STANDARD.md))
- Application runtime configuration files

---

## Mandatory Metadata Fields

Every project configuration file **must** include the following fields, using the syntax appropriate to its format.

### CF-01 — Project Name

The project name **must** be present. It **must** use lowercase letters and hyphens as separators. Underscores, spaces, and uppercase letters are not permitted.

| Correct | Incorrect |
|---|---|
| `psychoquine` | `PsychoQuine` |
| `core-red-standards` | `core_red_standards` |

### CF-02 — Description

A short, single-sentence description of the project **must** be present. The description **must** be factual and concise. It **must not** contain marketing language, subjective qualifiers, or version-specific claims.

### CF-03 — Version

A version field **must** be present. The version **must** follow semantic versioning as defined by Core Red standards (see [STANDARD_VERSION.md](../STANDARD_VERSION.md)).

The version field represents the current release version of the project. Pre-release identifiers (e.g., `0.1.0-alpha`) are permitted when the project has not reached stable release.

---

## Recommended Metadata Fields

The following fields are not mandatory but **should** be included when the format supports them.

| Field | Purpose |
|---|---|
| `license` | The license identifier (e.g., `MIT`). **Must** align with [LICENSE_POLICY.md](../LICENSE_POLICY.md). |
| `repository` | The URL of the project repository. |
| `authors` | The authoring entity or entities. For Core Red projects, use `Sxnnyside Project`. |
| `keywords` | A list of relevant terms for discoverability. |
| `homepage` | The project or organization homepage URL. |

---

## Formatting Rules

### CF-FMT-01 — No Extraneous Fields

Project configuration files **must not** include fields that serve no functional or informational purpose. Placeholder or aspirational fields with empty values are not permitted.

### CF-FMT-02 — Consistent Key Ordering

Fields **should** follow a consistent, logical order:

1. Project identity (name, version, description)
2. Authorship and licensing
3. Repository and homepage references
4. Dependencies and build configuration

### CF-FMT-03 — No Inline Comments in JSON

JSON files do not support comments. If documentation is required for a JSON configuration field, it **must** be provided in a companion documentation file or the project README.

### CF-FMT-04 — Comments in YAML and TOML

YAML and TOML files **should** include a leading comment that states the file's purpose. Section comments **may** be used to separate logical groups.

---

## Canonical Examples

### JSON (`package.json`)

```json
{
  "name": "psychoquine",
  "version": "0.1.0",
  "description": "Universal quine generator for arbitrary textual resources.",
  "license": "MIT",
  "repository": {
    "type": "git",
    "url": "https://github.com/Sxnnyside-Project/psychoquine.git"
  },
  "keywords": [
    "quine",
    "generator",
    "meta-programming"
  ]
}
```

### YAML (`pubspec.yaml`)

```yaml
# Project configuration for psychoquine.
name: psychoquine
version: 0.1.0
description: Universal quine generator for arbitrary textual resources.
homepage: https://github.com/Sxnnyside-Project/psychoquine
```

### TOML (`Cargo.toml`)

```toml
# Project configuration for psychoquine.
[package]
name = "psychoquine"
version = "0.1.0"
description = "Universal quine generator for arbitrary textual resources."
license = "MIT"
repository = "https://github.com/Sxnnyside-Project/psychoquine"
authors = ["Sxnnyside Project"]
edition = "2021"
```

---

## Compliance

A project configuration file is non-compliant if any of the following conditions are true:

- The project name is absent or does not follow the naming convention.
- The description is absent, empty, or contains marketing language.
- The version field is absent or does not follow semantic versioning.
- The license field, if present, contradicts the project's LICENSE file or the [LICENSE_POLICY.md](../LICENSE_POLICY.md).
- The file contains extraneous or placeholder fields with no functional purpose.

Non-compliance **must** be resolved before release.