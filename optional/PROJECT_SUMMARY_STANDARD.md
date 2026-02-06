# Project Summary Standard

This document defines the standard template for the PROJECT_SUMMARY file in Core Red repositories. The PROJECT_SUMMARY file is **optional**. It exists to provide a high-level, non-technical overview of a project intended for audiences who need to understand what the project is and why it exists, without reading the full README.

The PROJECT_SUMMARY is not a replacement for the README. It is a condensed reference that focuses on intent, scope, and outcomes rather than installation, usage, or development details. Where the README is the operational manual, the PROJECT_SUMMARY is the executive brief.

---

## When This Document Applies

A project **should** include a `PROJECT_SUMMARY.md` file when any of the following conditions are true:

- The project serves stakeholders beyond the development team (e.g., project managers, organizational leadership, external partners).
- The project is part of a multi-repository system where understanding inter-project relationships is necessary.
- The project's purpose or scope is frequently misunderstood or misrepresented.
- The README has grown complex enough that a shorter overview document would benefit onboarding.

A project **may** omit `PROJECT_SUMMARY.md` when the README Overview section is sufficient to communicate the project's purpose, scope, and audience to all relevant stakeholders.

---

## Template Structure

The PROJECT_SUMMARY file **must** contain the following sections, in this order. Sections marked as conditional **may** be omitted only when the stated condition applies.

1. Project Name
2. Purpose
3. Scope
4. Audience
5. Current Status
6. Key Outcomes
7. Related Projects (conditional: omit only if the project is standalone with no inter-project dependencies)
8. Points of Contact

---

## Section Requirements

### Project Name

The project name as an H1 heading, followed by a single subtitle line that captures the project's identity in one sentence. This **must** match the project name used in the README.

### Purpose

One to three paragraphs explaining why the project exists. The purpose section answers the question: "What problem does this project solve, and for whom?"

The purpose **must not** include implementation details, technical specifications, or usage instructions. It describes the motivation and the value delivered, not the mechanism.

### Scope

A clear statement of what the project covers and what it explicitly does not cover. The scope section **must** include:

- **In Scope**: A bulleted list of capabilities, responsibilities, or domains the project addresses.
- **Out of Scope**: A bulleted list of capabilities, responsibilities, or domains the project explicitly does not address.

The Out of Scope list is not optional when the In Scope list is present. Defining boundaries prevents scope creep and misaligned expectations.

### Audience

A description of who the project is intended for. The audience section **must** identify:

- The primary users or consumers of the project.
- The secondary users, if any (e.g., contributors, integrators, administrators).
- Any prerequisites the audience is expected to have (e.g., familiarity with a specific domain or technology).

### Current Status

A factual statement of the project's current lifecycle stage. Valid status values are:

| Status | Definition |
|---|---|
| Planning | Requirements gathering and design. No implementation has begun. |
| In Development | Active implementation. Not yet suitable for production use. |
| Alpha | Functional but incomplete. Breaking changes are expected. |
| Beta | Feature-complete for initial scope. Breaking changes are possible. |
| Stable | Released and production-ready. Follows semantic versioning. |
| Maintenance | Receiving bug fixes and security patches only. No new features planned. |
| Deprecated | No longer actively maintained. Users are directed to alternatives. |
| Archived | Read-only. No further changes will be made. |

The status **must** be one of the values in this table. The status **must** include a date indicating when the status was last updated.

### Key Outcomes

A bulleted list of the concrete, measurable outcomes the project delivers. Each outcome **must** be stated as a factual result, not a goal or aspiration.

Correct: "Generates changelog entries from commit history."
Incorrect: "Aims to make changelog management easier."

The Key Outcomes section replaces what other standards might call "Features" or "Highlights." It focuses on what the project produces, not what it contains.

### Related Projects

A table listing other projects that this project depends on, integrates with, or is consumed by.

| Project | Relationship | Description |
|---|---|---|
| `<RELATED_PROJECT_NAME>` | `<RELATIONSHIP_TYPE>` | `<RELATIONSHIP_DESCRIPTION>` |

Valid relationship types include: "depends on", "consumed by", "integrates with", "replaces", "extends", and "shares components with."

This section **may** be omitted if the project is entirely standalone with no inter-project dependencies or relationships.

### Points of Contact

A table listing the individuals or teams responsible for the project. Each entry **must** include a role, a name or team identifier, and a contact method.

| Role | Contact | Method |
|---|---|---|
| `<ROLE>` | `<CONTACT_NAME>` | `<CONTACT_METHOD>` |

Contact methods **must** use only canonical Sxnnyside Project contact channels as defined in the project's documentation standards. No personal email addresses, social media handles, or external communication platforms are permitted.

---

## Canonical Template

```markdown
# <PROJECT_NAME>

<PROJECT_SUBTITLE>

## Purpose

<PROJECT_PURPOSE>

## Scope

### In Scope

- <IN_SCOPE_ITEM>
- <IN_SCOPE_ITEM>
- <IN_SCOPE_ITEM>

### Out of Scope

- <OUT_OF_SCOPE_ITEM>
- <OUT_OF_SCOPE_ITEM>
- <OUT_OF_SCOPE_ITEM>

## Audience

<AUDIENCE_DESCRIPTION>

### Primary Users

- <PRIMARY_USER_GROUP>
- <PRIMARY_USER_GROUP>

### Secondary Users

- <SECONDARY_USER_GROUP>
- <SECONDARY_USER_GROUP>

### Prerequisites

- <PREREQUISITE>
- <PREREQUISITE>

## Current Status

**Status**: <PROJECT_STATUS>
**Last Updated**: <STATUS_DATE>

<STATUS_CONTEXT>

## Key Outcomes

- <OUTCOME>
- <OUTCOME>
- <OUTCOME>
- <OUTCOME>

## Related Projects

| Project | Relationship | Description |
|---|---|---|
| <RELATED_PROJECT_NAME> | <RELATIONSHIP_TYPE> | <RELATIONSHIP_DESCRIPTION> |
| <RELATED_PROJECT_NAME> | <RELATIONSHIP_TYPE> | <RELATIONSHIP_DESCRIPTION> |

## Points of Contact

| Role | Contact | Method |
|---|---|---|
| <ROLE> | <CONTACT_NAME> | <CONTACT_METHOD> |
| <ROLE> | <CONTACT_NAME> | <CONTACT_METHOD> |
```

---

## Placeholder Fields

| Placeholder | Description |
|---|---|
| `<PROJECT_NAME>` | The official name of the project. Must match the README. |
| `<PROJECT_SUBTITLE>` | A single sentence capturing the project's identity. |
| `<PROJECT_PURPOSE>` | One to three paragraphs explaining why the project exists. |
| `<IN_SCOPE_ITEM>` | A capability or domain the project addresses. |
| `<OUT_OF_SCOPE_ITEM>` | A capability or domain the project explicitly does not address. |
| `<AUDIENCE_DESCRIPTION>` | Introductory paragraph describing the project's intended audience. |
| `<PRIMARY_USER_GROUP>` | A primary consumer or user group of the project. |
| `<SECONDARY_USER_GROUP>` | A secondary user group (contributors, integrators, administrators). |
| `<PREREQUISITE>` | A knowledge or tool prerequisite expected of the audience. |
| `<PROJECT_STATUS>` | One of the defined lifecycle stages (Planning through Archived). |
| `<STATUS_DATE>` | ISO 8601 date when the status was last updated. |
| `<STATUS_CONTEXT>` | One to two sentences providing context for the current status. |
| `<OUTCOME>` | A concrete, measurable result the project delivers. |
| `<RELATED_PROJECT_NAME>` | The name of a related project. |
| `<RELATIONSHIP_TYPE>` | The nature of the relationship (depends on, consumed by, etc.). |
| `<RELATIONSHIP_DESCRIPTION>` | One-sentence description of how the projects relate. |
| `<ROLE>` | The role of the contact (e.g., Maintainer, Security Lead). |
| `<CONTACT_NAME>` | The name or team identifier of the contact. |
| `<CONTACT_METHOD>` | Canonical contact channel (email per organizational standards). |

---

## Compliance

A PROJECT_SUMMARY file is non-compliant if any of the following conditions are true:

- The project name does not match the README.
- The purpose section contains implementation details or technical specifications.
- The scope section is missing the Out of Scope subsection.
- The status value is not one of the defined lifecycle stages.
- The status date is missing or not in ISO 8601 format.
- Key outcomes are stated as goals or aspirations rather than factual results.
- The points of contact section uses non-canonical contact channels.
- The tone contains marketing, motivational, or emotional language.
- Placeholder fields have not been replaced with project-specific values.

Non-compliance **must** be resolved before release.