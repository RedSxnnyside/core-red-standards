# Environment Example File Standard

This document defines the standard for `.env.example` files across all Core Red projects. The `.env.example` file is a controlled artifact that documents the required and optional environment variables for a project.

---

## Purpose

The `.env.example` file serves as the canonical reference for environment configuration. It **must** contain every environment variable the project recognizes, organized and documented to eliminate ambiguity.

The `.env.example` file is committed to the repository. The `.env` file is not.

---

## File Requirements

### EE-01 — Mandatory Presence

Every Core Red project that uses environment variables **must** include a `.env.example` file at the repository root.

### EE-02 — No Real Credentials

The `.env.example` file **must not** contain real credentials, tokens, keys, passwords, or any sensitive values. All values **must** be placeholders.

### EE-03 — Placeholder Notation

Placeholder values **must** use one of the following formats:

| Type | Placeholder Format |
|---|---|
| Required variable, user-supplied | `your_value_here` |
| Required variable, generated | `generate_a_value` |
| URL with structure | `https://example.com/path` |
| Numeric value | The default value or `0` |
| Boolean value | `true` or `false` (whichever is the safe default) |

### EE-04 — Sync with Application

The `.env.example` file **must** be updated whenever an environment variable is added, removed, or renamed in the application. Drift between the application and the `.env.example` file is a compliance failure.

---

## Ordering Rules

### EO-01 — Grouped by Domain

Variables **must** be grouped by functional domain (e.g., database, authentication, logging). Each group **must** be preceded by a section comment.

### EO-02 — Required Before Optional

Within each group, required variables **must** appear before optional variables.

### EO-03 — Alphabetical Within Groups

Variables within a group **should** be ordered alphabetically unless a logical dependency dictates otherwise (e.g., `DB_HOST` before `DB_PORT`).

---

## Comment Rules

### EC-01 — Section Headers

Each group of related variables **must** be preceded by a comment line in the format:

```bash
# --- Section Name ---
```

### EC-02 — Required and Optional Markers

Each variable **must** include a comment indicating whether it is required or optional:

```bash
# Required: Description of the variable.
# Optional: Description of the variable. Defaults to <default_value>.
```

### EC-03 — No Inline Comments After Values

Comments **must** appear on the line above the variable, not inline after the value.

| Correct | Incorrect |
|---|---|
| `# Required: Database hostname.` | `DB_HOST=localhost # database host` |
| `DB_HOST=localhost` | |

---

## Variable Naming

### EN-01 — SCREAMING_SNAKE_CASE

All environment variable names **must** use uppercase letters with underscores as separators.

### EN-02 — Prefix by Domain

Variables **should** be prefixed by their functional domain to prevent collisions.

| Correct | Incorrect |
|---|---|
| `DB_HOST` | `HOST` |
| `AUTH_SECRET` | `SECRET` |
| `LOG_LEVEL` | `LEVEL` |

---

## Canonical Template

```bash
# ============================================================
# Environment Configuration
# Project: [PROJECT_NAME]
# Standard: Core Red v1.0
# ============================================================

# --- Application ---

# Required: The environment the application runs in.
NODE_ENV=development

# Required: Port the application listens on.
PORT=3000

# --- Database ---

# Required: Database host address.
DB_HOST=localhost

# Required: Database port.
DB_PORT=5432

# Required: Database name.
DB_NAME=your_value_here

# Required: Database user.
DB_USER=your_value_here

# Required: Database password.
DB_PASSWORD=your_value_here

# --- Authentication ---

# Required: Secret used to sign tokens. Generate a secure random value.
AUTH_SECRET=generate_a_value

# Required: Token expiration time in seconds.
AUTH_TOKEN_EXPIRY=3600

# --- Logging ---

# Optional: Log level. Defaults to info.
LOG_LEVEL=info

# Optional: Log format. Defaults to json.
LOG_FORMAT=json

# --- External Services ---

# Optional: Third-party API base URL.
EXTERNAL_API_URL=https://example.com/api
```

---

## Compliance

A `.env.example` file is non-compliant if any of the following conditions are true:

- The file contains real credentials or sensitive values.
- A variable recognized by the application is missing from the file.
- Variables are not grouped by domain.
- Required and optional markers are absent.
- Variable names do not use `SCREAMING_SNAKE_CASE`.

Non-compliance **must** be resolved before release.