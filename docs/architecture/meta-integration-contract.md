# Meta Integration Contract

## Status

- Documentation state: `DOCUMENTED`
- Implementation state: `NOT_IMPLEMENTED`
- Live Meta validation: `NOT_VALIDATED`
- API product and version: `PENDING_SELECTION`
- Last reviewed: 2026-10-12

This is a contract template for future implementation. It does not assert
that a Meta API has been selected, that credentials exist, or that any request
has been made successfully.

## 1. Integration identity

Before implementation, record the following for each integration:

| Field | Required value |
| --- | --- |
| Business use case | `PENDING_DEFINITION` |
| Meta product | `PENDING_SELECTION` |
| API family | `PENDING_VERIFICATION` |
| Official documentation URL | `PENDING_VERIFICATION` |
| API version | `PENDING_SELECTION` |
| App and account ownership | `PENDING_VERIFICATION` |
| Environments | `PENDING_DEFINITION` |
| Business owner | `PENDING_ASSIGNMENT` |
| Technical owner | `PENDING_ASSIGNMENT` |
| Data classification | `PENDING_ASSESSMENT` |
| External validation evidence | `NONE` |

Do not substitute assumptions or an undocumented default for a required value.

## 2. Operation contract

Every proposed API operation must document:

- Stable internal operation name and business purpose.
- Official endpoint and HTTP method, verified for the selected API version.
- Required account, asset, and app context.
- Required permissions and the official basis for each permission.
- Request schema, required fields, constraints, and sensitive fields.
- Response schema and fields consumed by the application.
- Expected success and failure outcomes.
- Pagination, rate-limit behavior, timeout, and retry policy.
- Whether the operation causes an external side effect.
- Idempotency or duplicate-prevention strategy, where applicable.
- Logging, redaction, retention, and evidence requirements.
- Automated test coverage and live validation status.

Endpoint paths, permissions, and schemas remain unspecified until official
documentation and the use case have been reviewed.

## 3. Authentication and authorization

Authentication must be selected for the actual Meta product, account model,
and operation. Do not assume that one token type or OAuth flow works for all
Meta products.

Before enabling access:

1. Document the supported authentication flow using official documentation.
2. Identify each required permission and why it is necessary.
3. Confirm the app, account, business, and asset prerequisites.
4. Define token storage, access restrictions, rotation, revocation, and expiry
   handling.
5. Verify environment separation and ensure secrets cannot enter Git or logs.
6. Record the observed authorization result without exposing token values.

Least privilege is the default. A permission is not approved merely because
it appears in an example or is convenient during development.

## 4. API versioning and compatibility

- Pin an explicit API version for every implemented integration.
- Record the official version-specific documentation used.
- Do not silently switch to a newer version.
- Review breaking changes, deprecations, and migration requirements before
  changing the pinned version.
- Test request and response mappings against the selected version.
- Record the change, evidence, and rollback approach.

The actual version is `PENDING_SELECTION`; no version is claimed to be
compatible at this stage.

## 5. Errors, rate limits, and retries

Implement an explicit error classification based on the selected product's
official behavior.

At minimum, assess:

- Authentication or authorization failures.
- Invalid requests and business-rule rejections.
- Rate limiting and provider-directed retry delays.
- Transient network and provider failures.
- Timeouts with an unknown outcome.
- Unsupported versions, permissions, or capabilities.

Retry only when the operation and failure condition make retrying safe.
Use bounded attempts, timeouts, and backoff. Respect official retry guidance.
Do not blindly retry an operation that may already have caused an external
side effect. Where outcome is uncertain, define a reconciliation strategy.

Exact error codes and response fields must be verified against the selected
API documentation before implementation.

## 6. Webhooks and asynchronous processing

For each required event, document:

- Official subscription and configuration requirements.
- The official delivery-authentication and signature-verification mechanism.
- Required headers and raw-body handling, if applicable.
- Event schema and version assumptions.
- Duplicate delivery, ordering, replay, and retry behavior.
- Acknowledgement policy and processing timeout.
- Sensitive-field redaction and payload retention.
- Monitoring and recovery for failed event processing.

Do not implement signature verification from memory or from an unrelated
Meta product's examples. Confirm the exact mechanism for the selected product
against official documentation first.

Webhook support remains `PENDING_SELECTION`.

## 7. Data handling and privacy

Before processing real account or customer data, document:

- Data categories and purpose for each field collected.
- Whether personal, confidential, or regulated data may be present.
- Access controls and permitted processing environments.
- Minimization, retention, deletion, and backup handling.
- Redaction requirements for logs, test fixtures, and error reports.
- Applicable contractual and legal obligations, verified for the actual use.

Use synthetic or appropriately anonymized data for tests whenever feasible.
Do not store full provider payloads by default when a smaller evidence record
meets the operational need.

This document is not a legal or compliance assessment.

## 8. Testing and evidence

Keep these validation levels separate:

| Level | Evidence required |
| --- | --- |
| `DOCUMENTED` | Reviewed specification or contract in the repository. |
| `IMPLEMENTED` | Code exists and has been reviewed. |
| `TESTED` | Recorded automated or manual test results. |
| `VALIDATED_AGAINST_META` | Evidence from the relevant Meta interface and environment. |
| `DEPLOYED` | Evidence of deployment to a named environment. |

Mocked responses and local unit tests do not establish live Meta compatibility.
A successful authentication check does not prove that every operation or
permission works. Record the exact operation, API version, environment,
timestamp, outcome, and sanitized evidence for each external validation.

Never include access tokens, secrets, or unnecessary personal data in evidence.

## 9. Release and recovery

Before production use, define:

- Configuration and secret prerequisites.
- Permission and account prerequisites.
- Deployment and smoke-test procedure.
- Monitoring and alerting.
- Failure containment and safe retry behavior.
- Rollback or disablement procedure.
- Token revocation and incident response.
- Ownership and operational handover.

Production readiness remains unassessed until the implementation and its
operational controls have evidence.

## 10. Official verification register

For every selected API product, maintain a reviewed record of:

- Official documentation URL and access date.
- Product and API version.
- Endpoint and permission references.
- Authentication requirements.
- Rate-limit and error-handling guidance.
- Webhook requirements, if applicable.
- Deprecation or compatibility notes.
- Reviewer and unresolved questions.

Only official sources appropriate to the selected product should settle
product-specific behavior. Community examples may aid discovery but are not
the final authority for permissions or security-sensitive behavior.

## 11. Open questions blocking implementation

1. What is the first business workflow to support?
2. Which Meta product and API family does that workflow require?
3. Which accounts, businesses, and assets are in scope?
4. Which operations must read data and which may change external state?
5. Is asynchronous event delivery required?
6. What environment and deployment model will be used?
7. What data may be processed, and what retention is justified?
8. Who will own credentials, external validation, and operations?

Resolve these questions in order of dependency. Do not add scopes, endpoints,
or runtime dependencies until the corresponding decisions are documented.
