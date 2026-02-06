# Style Guide

This document defines the structural and stylistic rules for all documentation produced under Core Red standards. These rules apply to every Markdown document in every Core Red repository.

---

## Heading Hierarchy

### S-HEAD-01 — Single H1

Every document **must** contain exactly one first-level heading (`#`). It **must** be the first content line of the document.

### S-HEAD-02 — Sequential Nesting

Heading levels **must not** be skipped. An H3 (`###`) **must not** appear unless preceded by an H2 (`##`) in the same logical section.

### S-HEAD-03 — Descriptive Headings

Headings **must** describe the content of their section. Generic headings ("Miscellaneous", "Other", "Notes") are prohibited unless no more specific alternative exists.

### S-HEAD-04 — No Duplicate Headings

No two headings at the same level within a document **may** share identical text.

### S-HEAD-05 — No Terminal Punctuation

Headings **must not** end with periods, colons, or other punctuation marks. Question marks are permitted only in FAQ-structured sections.

---

## Section Ordering

### S-ORD-01 — Purpose First

Every document **should** open with a section that states the document's purpose or scope immediately after the H1 heading.

### S-ORD-02 — General to Specific

Content **must** progress from general concepts to specific details. High-level overviews precede implementation specifics.

### S-ORD-03 — Requirements Before Procedures

Prerequisite information (dependencies, permissions, environment requirements) **must** appear before procedural instructions.

### S-ORD-04 — Consistent Ordering Across Projects

Documents of the same type (e.g., all README files) **should** follow the same section order across projects, as defined by the applicable standard template.

---

## Sentence Structure

### S-SENT-01 — One Idea per Sentence

Each sentence **must** express a single idea. Compound sentences are permitted only when the clauses are directly and necessarily related.

### S-SENT-02 — Maximum Sentence Length

Sentences **should not** exceed 30 words. Sentences exceeding 40 words **must** be restructured.

### S-SENT-03 — Subject-Verb-Object Order

Standard English sentence order **must** be maintained. Inverted constructions are permitted only for emphasis in exceptional cases.

### S-SENT-04 — No Run-On Sentences

Run-on sentences and comma splices are prohibited. Use separate sentences or appropriate conjunctions.

### S-SENT-05 — Parallel Construction

Items in a list, options in a comparison, or steps in a procedure **must** use parallel grammatical structure.

---

## Formatting Rules

### S-FMT-01 — Bold for Emphasis

Bold (`**text**`) is the primary mechanism for emphasis. Italic (`*text*`) is reserved for titles of external works, introductions of defined terms, or placeholder values.

### S-FMT-02 — Inline Code for Technical References

Inline code (`` `text` ``) **must** be used for:

- File names and paths
- Command names
- Function, method, class, and variable names
- Configuration keys and values
- Package names

### S-FMT-03 — No Underline or Strikethrough

Underline and strikethrough formatting are not permitted in Core Red documentation.

### S-FMT-04 — Horizontal Rules as Section Separators

Horizontal rules (`---`) **may** be used to separate major sections. They **must not** be used for decorative purposes or within subsections.

### S-FMT-05 — One Blank Line Between Blocks

Exactly one blank line **must** separate paragraphs, headings, code blocks, lists, and other block-level elements.

### S-FMT-06 — No Trailing Whitespace

Lines **must not** contain trailing whitespace.

### S-FMT-07 — File Ends with Newline

Every file **must** end with a single newline character.

---

## Lists

### S-LIST-01 — Unordered Lists for Non-Sequential Items

Unordered lists **must** be used for items that have no inherent order. Hyphens (`-`) are the required marker. Asterisks (`*`) and plus signs (`+`) are not permitted as list markers.

### S-LIST-02 — Ordered Lists for Sequential Items

Ordered lists (`1.`, `2.`, etc.) **must** be used for procedural steps or items with explicit sequence.

### S-LIST-03 — Consistent List Item Punctuation

If any item in a list is a complete sentence, all items in that list **must** end with a period. If no item is a complete sentence, no item **should** end with a period.

### S-LIST-04 — Parallel Structure in Lists

All items within a single list **must** follow the same grammatical structure.

### S-LIST-05 — No Deeply Nested Lists

List nesting **must not** exceed two levels. If deeper hierarchy is required, restructure the content using headings or separate sections.

---

## Code Blocks

### S-CODE-01 — Language Annotation Required

All fenced code blocks **must** include a language identifier.

```bash
echo "correct"
```

Blocks without a language identifier are non-compliant.

### S-CODE-02 — Minimal and Functional Examples

Code examples **must** be minimal, complete, and functional. Placeholder code is permitted only when marked with explicit comments.

### S-CODE-03 — No Screenshots of Code

Code **must** be presented as text in fenced code blocks. Images or screenshots of code are not permitted.

---

## Tables

### S-TBL-01 — Tables for Structured Comparisons

Tables **should** be used for structured data with two or more columns. Single-column data **must** be presented as a list.

### S-TBL-02 — Header Row Required

All tables **must** include a header row.

### S-TBL-03 — Consistent Column Alignment

Column alignment **must** be consistent within a table. Left-alignment is the default.

---

## Notes and Callouts

### S-NOTE-01 — Blockquote Syntax

Notes, warnings, and callouts **must** use Markdown blockquote syntax (`>`).

### S-NOTE-02 — Labeled Callouts

Callouts **must** be prefixed with a bold label indicating their type:

- **Note:** — Supplementary information
- **Warning:** — Potential for error or data loss
- **Important:** — Critical information that affects correctness

### S-NOTE-03 — No Decorative Callouts

Callouts **must not** be used for emphasis alone. They are reserved for information that falls outside the normal flow of the document and carries operational significance.

---

## Links

### S-LINK-01 — Descriptive Link Text

Link text **must** describe the destination. Bare URLs and generic text ("click here", "this link") are prohibited.

| Correct | Incorrect |
|---|---|
| See the [contributing guidelines](CONTRIBUTING.md). | Click [here](CONTRIBUTING.md). |

### S-LINK-02 — Relative Paths for Internal Links

Links to files within the same repository **must** use relative paths.

### S-LINK-03 — No Broken Links

All links **must** resolve to valid targets at the time of commit. Broken links are a compliance failure.