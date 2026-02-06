# Gitignore Standard

This document defines the standard structure, ordering, and content expectations for `.gitignore` files across all Core Red projects.

---

## Purpose

The `.gitignore` file prevents untracked and generated artifacts from entering version control. A well-structured `.gitignore` reduces repository noise, prevents credential leaks, and ensures consistent behavior across development environments.

---

## File Requirements

### GI-01 — Mandatory Presence

Every Core Red repository **must** include a `.gitignore` file at the repository root.

### GI-02 — Section-Based Organization

Entries **must** be organized into clearly labeled sections. Each section **must** be preceded by a comment header.

### GI-03 — Comment Format

Section headers **must** use the following format:

```bash
# --- Section Name ---
```

### GI-04 — No Empty Sections

Sections with no entries **must** be removed. Placeholder sections are not permitted.

### GI-05 — No Duplicate Entries

Each pattern **must** appear only once in the file. Redundant entries across sections **must** be consolidated.

---

## Ordering Rules

Sections **must** appear in the following order:

1. Operating system artifacts
2. Editor and IDE files
3. Environment and credentials
4. Build output
5. Dependencies
6. Language-specific artifacts
7. Project-specific entries

---

## Global Ignore Rules

The following patterns **must** appear in every Core Red `.gitignore` file, regardless of the project language or stack.

### Operating System Artifacts

```gitignore
# --- Operating System ---
.DS_Store
Thumbs.db
Desktop.ini
```

### Editor and IDE Files

```gitignore
# --- Editor / IDE ---
.vscode/
.idea/
*.swp
*.swo
*~
```

### Environment and Credentials

```gitignore
# --- Environment ---
.env
.env.local
.env.*.local
```

---

## Language-Specific Sections

Projects **must** include the applicable language-specific patterns. The following are canonical examples for supported stacks. Projects **may** extend these patterns but **must not** omit them.

### JavaScript / Node.js

```gitignore
# --- Node.js ---
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.pnpm-debug.log*
dist/
build/
coverage/
.cache/
```

### Python

```gitignore
# --- Python ---
__pycache__/
*.py[cod]
*$py.class
*.egg-info/
dist/
build/
.eggs/
*.egg
.venv/
venv/
.pytest_cache/
.mypy_cache/
htmlcov/
```

### Rust

```gitignore
# --- Rust ---
target/
Cargo.lock
**/*.rs.bk
```

> **Note:** `Cargo.lock` **should** be committed for binary projects and ignored for library projects, per Rust conventions. Adjust this entry based on the project type.

### C / C++

```gitignore
# --- C / C++ ---
*.o
*.obj
*.so
*.dylib
*.dll
*.a
*.lib
*.exe
*.out
build/
cmake-build-*/
```

---

## Project-Specific Entries

Patterns unique to the project (e.g., generated files, local scripts, temporary data directories) **must** be placed in a final section.

```gitignore
# --- Project ---
tmp/
local-data/
```

This section **must** only contain entries that do not belong to any of the preceding categories.

---

## Canonical Example

The following is a complete `.gitignore` for a Node.js project:

```gitignore
# --- Operating System ---
.DS_Store
Thumbs.db
Desktop.ini

# --- Editor / IDE ---
.vscode/
.idea/
*.swp
*.swo
*~

# --- Environment ---
.env
.env.local
.env.*.local

# --- Node.js ---
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.pnpm-debug.log*
dist/
build/
coverage/
.cache/

# --- Project ---
tmp/
```

---

## Compliance

A `.gitignore` file is non-compliant if any of the following conditions are true:

- The file is absent from the repository root.
- Global ignore rules (operating system, editor, environment) are missing.
- Entries are not organized into labeled sections.
- Duplicate entries exist.
- Language-specific patterns for the project's primary language are absent.

Non-compliance **must** be resolved before release.