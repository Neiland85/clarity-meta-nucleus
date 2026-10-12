# Platform Capability Matrix

- Baseline date: 2026-10-12
- Status: DISCOVERY
- Purpose: Prioritize integrations by workflow and verified provider capability.

## Capability status vocabulary

- PENDING: Requirements or use case have not been assessed.
- DOCUMENTED: Relevant official requirements have been recorded.
- ACCESS_PENDING: Required provider access, approval or credentials are outstanding.
- IMPLEMENTED: Code exists for the explicitly defined scope.
- VALIDATED: Acceptance evidence demonstrates that the defined scope works.
- DEPRECATED: The capability is being retired or is no longer supported.

Status applies to a specific product and use case, not to a provider as a whole.
DOCUMENTED does not mean IMPLEMENTED or VALIDATED.

## Initial capability matrix

All cells start as PENDING. Update them only after recording the relevant
official sources and requirements in the source register.

| Provider | Content publishing | Paid advertising | Analytics / insights | Catalog / products | Orders / inventory | Events / conversions |
|---|---|---|---|---|---|---|
| Meta: Facebook / Instagram | PENDING | PENDING | PENDING | PENDING | PENDING | PENDING |
| TikTok | PENDING | PENDING | PENDING | PENDING | PENDING | PENDING |
| Google Ads | PENDING | PENDING | PENDING | PENDING | PENDING | PENDING |
| YouTube | PENDING | PENDING | PENDING | PENDING | PENDING | PENDING |
| Shopify | PENDING | PENDING | PENDING | PENDING | PENDING | PENDING |
| WooCommerce | PENDING | PENDING | PENDING | PENDING | PENDING | PENDING |
| Pinterest | PENDING | PENDING | PENDING | PENDING | PENDING | PENDING |
| LinkedIn | PENDING | PENDING | PENDING | PENDING | PENDING | PENDING |

## Provisional research order

1. Meta: Facebook and Instagram.
2. TikTok.
3. Google Ads.
4. Shopify and WooCommerce.
5. YouTube.
6. Pinterest.
7. LinkedIn and other marketplaces, based on confirmed business demand.

This order is provisional. It does not establish access, approval or feasibility.

## Research requirements per capability

Before moving a cell from PENDING to DOCUMENTED, record:

- Business workflow and intended outcome.
- Exact provider API product and relevant endpoint/resource.
- Whether the operation reads data, writes data, or both.
- Authentication model and required scopes/permissions.
- Account eligibility, app review and access restrictions.
- Versioning, quotas, pagination and rate-limit behavior.
- Error handling, retries, idempotency and webhook behavior where applicable.
- Data minimization, retention, deletion and authorization implications.
- Test strategy and evidence required for VALIDATED.
- Source register references and unresolved questions.

## Architecture constraints

- Keep business-domain logic independent of provider SDKs and API models.
- Define contracts per capability; do not assume provider feature parity.
- Keep publishing, advertising, analytics, commerce and event tracking distinct.
- Isolate authentication, permissions, rate limits and versioning behind adapters.
- Do not claim cross-platform parity until each capability has evidence.
- Never commit credentials, access tokens or customer data in this matrix.
