# System Integration Standard

This document defines the standard template for the SYSTEM_INTEGRATION file in Core Red repositories. The SYSTEM_INTEGRATION file is **optional**. It is required only when the project depends on, communicates with, or is consumed by external systems.

An "external system" is any service, API, database, message broker, file system, or third-party platform that the project interacts with but does not own. Internal module boundaries are not external integrations and are documented in the ARCHITECTURE file.

This standard ensures that integration boundaries, contracts, failure modes, and ownership are documented explicitly. Undocumented integrations are the primary source of production incidents caused by assumptions rather than failures.

---

## When This Document Applies

A project **must** include a `SYSTEM_INTEGRATION.md` file when any of the following conditions are true:

- The project makes network calls to one or more external services.
- The project reads from or writes to an external database or data store not managed by the project itself.
- The project consumes messages from or publishes messages to an external message broker.
- The project depends on external authentication, authorization, or identity providers.
- The project is deployed as part of a multi-service system where other services depend on its outputs.

A project **may** omit `SYSTEM_INTEGRATION.md` when it is entirely self-contained — that is, it performs no network I/O, accesses no external data stores, and is not consumed by other services.

---

## Template Structure

The SYSTEM_INTEGRATION file **must** contain the following sections, in this order. Sections marked as conditional **may** be omitted only when the stated condition applies.

1. Overview
2. Integration Inventory
3. Integration Details (one subsection per integration)
4. Authentication and Authorization
5. Failure Modes and Resilience
6. Environment Configuration
7. Dependency Assumptions
8. Monitoring and Observability (conditional: omit only if the project has no production deployment)

---

## Section Requirements

### Overview

One to two paragraphs summarizing the project's integration landscape. The overview **must** state:

- How many external systems the project integrates with.
- The general nature of these integrations (e.g., "consumes REST APIs", "publishes to a message queue", "reads from a shared database").
- Which integrations are critical (failure causes the project to stop functioning) versus optional (failure degrades but does not prevent operation).

### Integration Inventory

A summary table listing all external integrations. This table provides a quick reference before the reader encounters the detailed subsections.

| Integration | Type | Direction | Criticality | Owner |
|---|---|---|---|---|
| `<INTEGRATION_NAME>` | `<INTEGRATION_TYPE>` | `<DIRECTION>` | `<CRITICALITY>` | `<OWNER>` |

Column definitions:

- **Integration**: The name of the external system.
- **Type**: The protocol or mechanism (e.g., REST API, gRPC, PostgreSQL, Redis, RabbitMQ, file system, S3).
- **Direction**: "Inbound" (external system calls this project), "Outbound" (this project calls external system), or "Bidirectional."
- **Criticality**: "Critical" (project cannot function without it) or "Optional" (project degrades gracefully without it).
- **Owner**: The team or organization responsible for the external system.

### Integration Details

Each external integration **must** have its own H3 subsection under this heading. Each subsection **must** include:

- **System**: The full name and version (if applicable) of the external system.
- **Protocol**: The communication protocol (e.g., HTTPS, gRPC, AMQP, TCP).
- **Endpoint**: The base URL, hostname, or connection string. Use placeholders for environment-specific values.
- **Authentication**: How this project authenticates with the external system (e.g., API key, OAuth 2.0, mTLS, database credentials).
- **Data Contract**: What data this project sends to and receives from the external system. Include request and response schemas or describe the message format.
- **Rate Limits**: Any rate limits imposed by the external system, and how the project respects them.
- **Timeout Configuration**: The configured timeout for this integration and the rationale for the chosen value.
- **Retry Policy**: How the project handles transient failures for this integration (e.g., exponential backoff with jitter, fixed retry count, circuit breaker).

Format:

```markdown
### <INTEGRATION_NAME>

- **System**: <SYSTEM_NAME_AND_VERSION>
- **Protocol**: <PROTOCOL>
- **Endpoint**: `<ENDPOINT>`
- **Authentication**: <AUTHENTICATION_METHOD>
- **Data Contract**:
  - Request: <REQUEST_DESCRIPTION>
  - Response: <RESPONSE_DESCRIPTION>
- **Rate Limits**: <RATE_LIMIT_DESCRIPTION>
- **Timeout**: <TIMEOUT_VALUE> — <TIMEOUT_RATIONALE>
- **Retry Policy**: <RETRY_POLICY_DESCRIPTION>
```

### Authentication and Authorization

A consolidated section describing all authentication and authorization mechanisms used across integrations. This section exists to prevent credential management from being scattered across individual integration descriptions.

This section **must** include:

- Where credentials are stored (e.g., environment variables, secrets manager, configuration files).
- How credentials are rotated.
- Which credentials are shared across integrations and which are integration-specific.
- Any service accounts or machine identities used by the project.

Credentials **must not** appear in this file. Only the mechanism and storage location are documented.

### Failure Modes and Resilience

A table documenting the expected failure modes for each integration and the project's response to each failure.

| Integration | Failure Mode | Impact | Response |
|---|---|---|---|
| `<INTEGRATION_NAME>` | `<FAILURE_MODE>` | `<IMPACT>` | `<RESPONSE>` |

Column definitions:

- **Integration**: The name of the external system.
- **Failure Mode**: The type of failure (e.g., timeout, connection refused, 5xx response, invalid response body, rate limit exceeded).
- **Impact**: What happens to the project when this failure occurs.
- **Response**: How the project handles this failure (e.g., retry, fallback, circuit break, graceful degradation, hard failure).

Every critical integration **must** have at least two documented failure modes: timeout and complete unavailability.

### Environment Configuration

A table listing all environment variables or configuration values required for external integrations.

| Variable | Integration | Required | Default | Description |
|---|---|---|---|---|
| `<VARIABLE_NAME>` | `<INTEGRATION_NAME>` | `<REQUIRED>` | `<DEFAULT>` | `<VARIABLE_DESCRIPTION>` |

This section **must** align with the `.env.example` file. If a variable is documented here, it **must** appear in `.env.example`, and vice versa for integration-related variables.

### Dependency Assumptions

A bulleted list of assumptions the project makes about its external dependencies. Each assumption **must** be stated as a factual claim that, if violated, would cause the integration to fail.

Examples of valid assumptions:

- The `<SERVICE_NAME>` API returns responses within `<TIMEOUT_VALUE>` under normal load.
- The `<DATABASE_NAME>` schema includes the `<TABLE_NAME>` table with the columns defined in the data contract.
- The `<MESSAGE_BROKER>` guarantees at-least-once delivery for the `<QUEUE_NAME>` queue.
- The `<AUTH_PROVIDER>` token endpoint is available at `<ENDPOINT>` and accepts client credentials grants.

This section is critical for diagnosing integration failures. When an assumption is violated, this list provides the first place to check.

### Monitoring and Observability

This section documents how integration health is monitored. It **must** include:

- What metrics are collected for each integration (e.g., latency, error rate, throughput).
- Where these metrics are reported (e.g., logging system, metrics dashboard, alerting platform).
- What alerting thresholds are configured.
- How to access integration health dashboards or logs.

This section **may** be omitted if the project has no production deployment — that is, if it is a library, a CLI tool used only locally, or a development-only utility.

---

## Canonical Template

```markdown
# System Integration

## Overview

<INTEGRATION_OVERVIEW>

## Integration Inventory

| Integration | Type | Direction | Criticality | Owner |
|---|---|---|---|---|
| <INTEGRATION_NAME> | <INTEGRATION_TYPE> | <DIRECTION> | <CRITICALITY> | <OWNER> |
| <INTEGRATION_NAME> | <INTEGRATION_TYPE> | <DIRECTION> | <CRITICALITY> | <OWNER> |

## Integration Details

### <INTEGRATION_NAME>

- **System**: <SYSTEM_NAME_AND_VERSION>
- **Protocol**: <PROTOCOL>
- **Endpoint**: `<ENDPOINT>`
- **Authentication**: <AUTHENTICATION_METHOD>
- **Data Contract**:
  - Request: <REQUEST_DESCRIPTION>
  - Response: <RESPONSE_DESCRIPTION>
- **Rate Limits**: <RATE_LIMIT_DESCRIPTION>
- **Timeout**: <TIMEOUT_VALUE> — <TIMEOUT_RATIONALE>
- **Retry Policy**: <RETRY_POLICY_DESCRIPTION>

### <INTEGRATION_NAME>

- **System**: <SYSTEM_NAME_AND_VERSION>
- **Protocol**: <PROTOCOL>
- **Endpoint**: `<ENDPOINT>`
- **Authentication**: <AUTHENTICATION_METHOD>
- **Data Contract**:
  - Request: <REQUEST_DESCRIPTION>
  - Response: <RESPONSE_DESCRIPTION>
- **Rate Limits**: <RATE_LIMIT_DESCRIPTION>
- **Timeout**: <TIMEOUT_VALUE> — <TIMEOUT_RATIONALE>
- **Retry Policy**: <RETRY_POLICY_DESCRIPTION>

## Authentication and Authorization

<AUTH_OVERVIEW>

### Credential Storage

<CREDENTIAL_STORAGE_DESCRIPTION>

### Credential Rotation

<CREDENTIAL_ROTATION_DESCRIPTION>

### Service Accounts

| Account | Integration | Purpose |
|---|---|---|
| <SERVICE_ACCOUNT> | <INTEGRATION_NAME> | <ACCOUNT_PURPOSE> |

## Failure Modes and Resilience

| Integration | Failure Mode | Impact | Response |
|---|---|---|---|
| <INTEGRATION_NAME> | <FAILURE_MODE> | <IMPACT> | <RESPONSE> |
| <INTEGRATION_NAME> | <FAILURE_MODE> | <IMPACT> | <RESPONSE> |
| <INTEGRATION_NAME> | <FAILURE_MODE> | <IMPACT> | <RESPONSE> |

## Environment Configuration

| Variable | Integration | Required | Default | Description |
|---|---|---|---|---|
| <VARIABLE_NAME> | <INTEGRATION_NAME> | <REQUIRED> | <DEFAULT> | <VARIABLE_DESCRIPTION> |
| <VARIABLE_NAME> | <INTEGRATION_NAME> | <REQUIRED> | <DEFAULT> | <VARIABLE_DESCRIPTION> |

## Dependency Assumptions

- <ASSUMPTION>
- <ASSUMPTION>
- <ASSUMPTION>
- <ASSUMPTION>

## Monitoring and Observability

### Metrics

| Integration | Metric | Threshold | Alert |
|---|---|---|---|
| <INTEGRATION_NAME> | <METRIC_NAME> | <THRESHOLD_VALUE> | <ALERT_DESCRIPTION> |

### Dashboards

- <DASHBOARD_DESCRIPTION>

### Log Access

- <LOG_ACCESS_DESCRIPTION>
```

---

## Placeholder Fields

| Placeholder | Description |
|---|---|
| `<INTEGRATION_OVERVIEW>` | One to two paragraphs summarizing the integration landscape. |
| `<INTEGRATION_NAME>` | The name of the external system. |
| `<INTEGRATION_TYPE>` | Protocol or mechanism (REST API, gRPC, PostgreSQL, etc.). |
| `<DIRECTION>` | Inbound, Outbound, or Bidirectional. |
| `<CRITICALITY>` | Critical or Optional. |
| `<OWNER>` | Team or organization responsible for the external system. |
| `<SYSTEM_NAME_AND_VERSION>` | Full name and version of the external system. |
| `<PROTOCOL>` | Communication protocol (HTTPS, gRPC, AMQP, TCP). |
| `<ENDPOINT>` | Base URL, hostname, or connection string (use placeholders for env-specific values). |
| `<AUTHENTICATION_METHOD>` | How the project authenticates with the external system. |
| `<REQUEST_DESCRIPTION>` | Schema or format of data sent to the external system. |
| `<RESPONSE_DESCRIPTION>` | Schema or format of data received from the external system. |
| `<RATE_LIMIT_DESCRIPTION>` | Rate limits imposed by the external system and how they are respected. |
| `<TIMEOUT_VALUE>` | Configured timeout duration. |
| `<TIMEOUT_RATIONALE>` | Rationale for the chosen timeout value. |
| `<RETRY_POLICY_DESCRIPTION>` | How transient failures are handled (backoff strategy, retry count, circuit breaker). |
| `<AUTH_OVERVIEW>` | Summary of authentication and authorization mechanisms. |
| `<CREDENTIAL_STORAGE_DESCRIPTION>` | Where and how credentials are stored. |
| `<CREDENTIAL_ROTATION_DESCRIPTION>` | How and when credentials are rotated. |
| `<SERVICE_ACCOUNT>` | Service account or machine identity name. |
| `<ACCOUNT_PURPOSE>` | Purpose of the service account. |
| `<FAILURE_MODE>` | Type of failure (timeout, connection refused, 5xx, rate limit exceeded). |
| `<IMPACT>` | Effect on the project when the failure occurs. |
| `<RESPONSE>` | How the project handles the failure. |
| `<VARIABLE_NAME>` | Environment variable name. |
| `<REQUIRED>` | Whether the variable is required (Yes or No). |
| `<DEFAULT>` | Default value, if any, or "None." |
| `<VARIABLE_DESCRIPTION>` | Description of the variable's purpose. |
| `<ASSUMPTION>` | A factual assumption about an external dependency. |
| `<METRIC_NAME>` | Name of the monitored metric (latency, error rate, throughput). |
| `<THRESHOLD_VALUE>` | Value at which an alert is triggered. |
| `<ALERT_DESCRIPTION>` | What happens when the threshold is exceeded. |
| `<DASHBOARD_DESCRIPTION>` | How to access the integration health dashboard. |
| `<LOG_ACCESS_DESCRIPTION>` | How to access integration-related logs. |

---

## Compliance

A SYSTEM_INTEGRATION file is non-compliant if any of the following conditions are true:

- The file is required (per the applicability criteria) but absent.
- The integration inventory table is missing or incomplete.
- An external integration exists in the codebase but is not documented in this file.
- Authentication mechanisms are described without documenting credential storage and rotation.
- A critical integration has no documented failure modes.
- Environment variables required for integrations are not documented or do not align with `.env.example`.
- Credentials, API keys, tokens, or secrets appear in the file.
- Dependency assumptions are absent when external dependencies exist.
- The tone contains marketing, motivational, or emotional language.
- Placeholder fields have not been replaced with project-specific values.

Non-compliance **must** be resolved before release.