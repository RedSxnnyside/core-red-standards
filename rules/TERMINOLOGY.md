# Terminology

This document standardizes the language used across all Core Red projects. Consistent terminology reduces ambiguity, improves searchability, and ensures documentation is interpretable without context-dependent assumptions.

All contributors **must** use the terms defined here. Deviation is non-compliant.

---

## Preferred Terms

The following are the canonical terms for Core Red documentation. Use only the preferred form.

| Preferred Term | Do Not Use |
|---|---|
| repository | repo, project folder, codebase (when referring to the Git repository) |
| project | app, application (when referring to the overall initiative) |
| application | app (in documentation text; `app` is permitted in code and CLI references) |
| dependency | dep, package (when referring to external requirements) |
| configuration | config (in documentation text; `config` is permitted in file names and code) |
| documentation | docs (in documentation text; `docs/` is permitted as a directory name) |
| environment variable | env var, env variable |
| pull request | PR, merge request (in documentation text; abbreviation is permitted in commit messages) |
| issue | bug, ticket (when referring to GitHub Issues) |
| release | deploy, ship (when referring to a versioned publication) |
| contributor | developer, user (when referring to someone contributing to the project) |
| maintainer | owner, admin (when referring to someone with merge authority) |
| endpoint | route, URL (when referring to an API endpoint) |
| credential | secret, key (when referring to authentication material; use specific terms like "API key" or "access token" when applicable) |

---

## Disallowed Terms

The following terms are **prohibited** in all Core Red documentation:

| Disallowed Term | Reason | Replacement |
|---|---|---|
| easy, simple | Subjective; uninformative | Remove or describe the actual steps |
| powerful | Marketing language | Describe the specific capability |
| robust | Vague | Specify the property (fault-tolerant, validated, etc.) |
| cutting-edge, state-of-the-art | Marketing language | Remove |
| seamless | Vague; typically inaccurate | Describe the integration method |
| leverage | Corporate jargon | Use "use" |
| utilize | Unnecessarily formal | Use "use" |
| please | Unnecessary courtesy in technical writing | Remove; use imperative mood |
| world-class | Marketing language | Remove |
| next-generation | Marketing language | Remove |
| out of the box | Colloquial | Use "by default" or "without additional configuration" |
| best-in-class | Marketing language | Remove |
| game-changing | Marketing language | Remove |

---

## Reserved Words

The following terms have specific meanings within Core Red and **must not** be used outside their defined context:

| Term | Reserved Meaning |
|---|---|
| Core Red | The organizational identity. Always written as two words, both capitalized. Never "CoreRed", "corered", "core-red", or "CORE RED" in documentation text. The hyphenated lowercase form `core-red` is permitted only in repository names, package names, and URLs. |
| standard | A normative requirement defined in this repository. Do not use "standard" to mean "typical" or "usual." |
| compliant | Meeting all mandatory requirements of the applicable Core Red standard. |
| mandatory | Required without exception. |
| optional | Permitted but not required; explicitly designated as such. |
| normative | Having the force of a requirement. |

---

## Consistency Rules

### T-CON-01 — Singular Nouns for Document References

When referring to a document type, use the singular form.

| Correct | Incorrect |
|---|---|
| Every project must include a README. | Every project must include READMEs. |
| The contributing guide defines the process. | The contributing guides define the process. |

Exception: plural is permitted when referring to multiple instances across projects ("All project READMEs must comply.").

### T-CON-02 — Capitalization of Document Names

Standard document names are written in all caps when referring to the filename: README, SECURITY, CONTRIBUTING, LICENSE, CHANGELOG.

When referring to the concept rather than the file, use lowercase: "the readme", "the security policy", "the contributing guide."

### T-CON-03 — Capitalization of Core Red

"Core Red" is always capitalized as a proper noun.

- Correct: "Core Red standards require..."
- Incorrect: "core red standards require..."

In repository names, URLs, and package identifiers, the hyphenated lowercase form `core-red` is used.

### T-CON-04 — No Abbreviations Without Definition

Abbreviations **must** be defined on first use within each document. Subsequent uses may use the abbreviation alone.

Exception: universally understood abbreviations (URL, API, CLI, HTML, CSS, JSON) do not require definition.

### T-CON-05 — American English Spelling

All Core Red documentation **must** use American English spelling.

| Correct | Incorrect |
|---|---|
| color | colour |
| behavior | behaviour |
| organization | organisation |
| license | licence |
| analyze | analyse |

### T-CON-06 — Dates

Dates **must** be written in ISO 8601 format: `YYYY-MM-DD`.

- Correct: 2026-02-06
- Incorrect: February 6, 2026; 06/02/2026; 02-06-2026

### T-CON-07 — Email Addresses

Email addresses referenced in documentation **must** use the full address format and **must** be presented as inline code.

- Correct: `security@sxnnysideproject.com`
- Incorrect: security at sxnnysideproject dot com

### T-CON-08 — URLs and Site References

URLs **must** be presented as functional Markdown links with descriptive text. Bare URLs are permitted only inside code blocks or configuration examples.

- Correct: See the [Sxnnyside Project site](https://sxnnysideproject.com) for details.
- Incorrect: See https://sxnnysideproject.com for details.

### T-CON-09 — Version References

Version numbers **must** use the `v` prefix followed by semantic versioning: `v1.0`, `v2.1.3`.

- Correct: v1.0
- Incorrect: version 1.0, Version 1, 1.0.0 (without prefix)

### T-CON-10 — Oxford Comma

The Oxford comma (serial comma) is **required** in all lists of three or more items.

- Correct: "README, SECURITY, and CONTRIBUTING"
- Incorrect: "README, SECURITY and CONTRIBUTING"