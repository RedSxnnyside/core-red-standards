# Document Tone

This document defines the required tone for all documentation produced under Core Red standards. Tone is a controlled attribute of every document and **must** be consistent across all Core Red projects.

---

## Allowed Tone Characteristics

All Core Red documentation **must** exhibit the following characteristics:

### Neutral

Documentation **must** present information without bias, enthusiasm, or subjective evaluation. The text serves the reader's need for accurate information, not the author's perspective.

### Professional

Language **must** reflect the standards of technical writing. Sentence construction, vocabulary, and formatting **must** be precise, structured, and free of informal constructs.

### Declarative

Statements **must** assert facts, requirements, or specifications. Documentation **must not** speculate, suggest possibilities, or leave conclusions to interpretation when a definitive statement is possible.

### Authoritative

Documentation **must** convey confidence in the information it presents. Hedging language ("might", "perhaps", "it seems") is prohibited unless uncertainty is a documented fact.

### Direct

Sentences **must** communicate their meaning without indirection. Circumlocution, filler phrases, and unnecessary qualification **must** be avoided.

### Technical

Terminology **must** be appropriate to the domain. Documentation **must not** simplify to the point of inaccuracy or omission.

---

## Disallowed Tone Characteristics

The following characteristics are **prohibited** in all Core Red documentation:

### Conversational

Informal phrasing, rhetorical questions, humor, slang, and colloquialisms are not permitted.

### Motivational

Encouragement, praise, inspirational framing, or aspirational language is not permitted. Documentation informs; it does not persuade or motivate.

### Marketing

Promotional language, superlatives ("best-in-class", "cutting-edge", "world-class"), and feature valorization are prohibited.

### Emotional

Expressions of excitement, frustration, urgency, gratitude, or sentiment **must not** appear in technical documentation.

### Apologetic

Apologies, disclaimers of inadequacy, or self-deprecating language are not permitted.

### Vague

Ambiguous qualifiers ("easy", "simple", "powerful", "flexible", "robust") are prohibited unless accompanied by measurable context or technical justification.

---

## Rules

### R-TONE-01 — No First-Person Singular

Documentation **must not** use "I" or "my."

First-person plural ("we") is permitted only in contributor-facing documents where it unambiguously refers to the project maintainers.

### R-TONE-02 — No Emotional Openers or Closers

Sentences such as "We're excited to announce", "Thank you for your interest", or "We'd love your help" are not permitted.

Opening and closing lines **must** be informational.

### R-TONE-03 — No Filler Phrases

The following phrases and their equivalents **must not** appear:

- "Please note that"
- "It is worth mentioning"
- "As you can see"
- "Basically"
- "Simply"
- "Just"
- "Obviously"
- "Actually"
- "In order to" (use "to")
- "At the end of the day"

### R-TONE-04 — Normative Language

Requirements **must** use normative keywords consistent with RFC 2119:

| Keyword | Meaning |
|---|---|
| **must** | Absolute requirement |
| **must not** | Absolute prohibition |
| **should** | Recommended; deviation requires justification |
| **should not** | Discouraged; deviation requires justification |
| **may** | Truly optional |

These keywords **must** be bold when used normatively.

### R-TONE-05 — Active Voice

Active voice is required unless passive voice demonstrably improves clarity or the agent is genuinely irrelevant.

| Correct | Incorrect |
|---|---|
| The system validates input before processing. | Input is validated before processing by the system. |
| Contributors must sign the CLA. | The CLA must be signed by contributors. |

### R-TONE-06 — Imperative Mood for Instructions

All procedural or instructional content **must** use imperative mood.

| Correct | Incorrect |
|---|---|
| Run the build command. | You should run the build command. |
| Clone the repository. | You can clone the repository. |

### R-TONE-07 — No Exclamation Marks

Exclamation marks are not permitted in Core Red documentation.

### R-TONE-08 — No Emojis

Emojis are not permitted in any Core Red documentation. This includes README files, security policies, changelogs, and inline comments within documentation.

---

## Scope of Application

### Public Documentation

Public-facing documentation (README, SECURITY, CONTRIBUTING, LICENSE references) **must** adhere strictly to all rules defined in this document. Public documentation is the external representation of the project and **must** convey precision and authority.

### Private Documentation

Internal documentation (architecture notes, developer memos, internal guides) **must** also adhere to all rules defined in this document.

The sole permitted relaxation for internal documentation is the use of established shorthand (e.g., ticket identifiers, internal project codes) where context is unambiguous.