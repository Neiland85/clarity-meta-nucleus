# Official Platform Source Register

- Baseline date: 2026-10-12
- Status: INITIAL — sources require verification against specific use cases.
- Purpose: Maintain traceable official evidence for platform integration decisions.

## Rules

1. Prefer official provider documentation for API contracts, authentication,
   permissions, quotas, versioning, review requirements and deprecations.
2. Secondary sources may help discover topics but must not be the sole evidence
   for a production integration decision.
3. Record the exact product, URL, date checked, relevant claim and API version.
4. Public documentation does not prove that our application has access,
   approval, credentials or permission to use a capability.
5. Re-check volatile requirements before implementation and release.
6. If a claim has not been inspected, mark it PENDING_VERIFICATION.
7. Do not generalize a restriction for one endpoint or product to an entire platform.

## Status definitions

- VERIFIED: The official source was inspected and supports the recorded claim.
- PENDING_VERIFICATION: The URL or claim has not yet been fully verified.
- SUPERSEDED: A newer official source or version replaces this entry.
- NOT_APPLICABLE: The source was reviewed and does not apply to the selected use case.

## Initial source inventory

| Provider | Product / area | Official source | Status | Follow-up |
|---|---|---|---|---|
| Meta | Graph API | https://developers.facebook.com/docs/graph-api/ | PENDING_VERIFICATION | Check versioning, tokens, permissions, errors and limits |
| Meta | Instagram Platform | https://developers.facebook.com/docs/instagram-platform/ | PENDING_VERIFICATION | Check account eligibility, publishing, insights and permissions |
| Meta | Marketing API | https://developers.facebook.com/docs/marketing-apis/ | PENDING_VERIFICATION | Check business access, app review and advertising permissions |
| TikTok | Developer documentation | https://developers.tiktok.com/doc/ | PENDING_VERIFICATION | Identify required API products |
| TikTok | Content Posting API | https://developers.tiktok.com/docs/content-posting-api-get-started | PENDING_VERIFICATION | Check authorization, scopes, audit and visibility restrictions |
| TikTok | App review | https://developers.tiktok.com/docs/app-review-guidelines | PENDING_VERIFICATION | Check review and application requirements |
| Google | Google Ads OAuth | https://developers.google.com/google-ads/api/docs/oauth/overview | PENDING_VERIFICATION | Check OAuth and developer-token access |
| Google | Google Ads quotas | https://developers.google.com/google-ads/api/docs/best-practices/quotas | PENDING_VERIFICATION | Check applicable quotas and retry guidance |
| YouTube | Data API | https://developers.google.com/youtube/v3/getting-started | PENDING_VERIFICATION | Check OAuth, quota and compliance requirements |
| Shopify | API versioning | https://shopify.dev/docs/api/usage/versioning | PENDING_VERIFICATION | Check supported versions and upgrade policy |
| WooCommerce | REST API | https://developer.woocommerce.com/docs/apis/rest-api/ | PENDING_VERIFICATION | Check API version, authentication and resources |
| WooCommerce | Authentication | https://developer.woocommerce.com/docs/apis/rest-api/authentication | PENDING_VERIFICATION | Check HTTPS and credential requirements |
| WooCommerce | Webhooks | https://developer.woocommerce.com/docs/apis/rest-api/v3/webhooks/ | PENDING_VERIFICATION | Check signatures and delivery behavior |
| Pinterest | Rate limits | https://developers.pinterest.com/docs/reference/rate-limits/ | PENDING_VERIFICATION | Check quotas and current API guidance |
| LinkedIn | Community Management | https://learn.microsoft.com/en-us/linkedin/marketing/community-management/community-management-overview | PENDING_VERIFICATION | Check access tiers, reviews and version lifecycle |

## Evidence record template

For every source used to justify a decision, record:

- Provider and exact API product
- Official URL and page title
- Date checked (YYYY-MM-DD)
- API version or versioning policy, where applicable
- Exact requirement or limitation observed
- Relevant capability and intended use case
- Required scopes, review and access prerequisites
- Evidence status and reviewer
- Related architecture decision or issue
- Next review trigger or date

## Limitations

This is an initial discovery register, not a completed platform audit.
All entries remain PENDING_VERIFICATION until inspected against a concrete use case.

## Initial verification log

These checks record specific official pages inspected on 2026-10-12.
They do not constitute a complete API assessment or establish application access.

### TikTok — Content Posting API

- Source: https://developers.tiktok.com/docs/en/content-posting-api-get-started
- Checked on: 2026-10-12
- Finding: Direct posting requires a registered application, the Content Posting
  API product, approval for the `video.publish` scope, and authorization by the
  target user. Unaudited clients are restricted to private visibility.
- Scope: Direct content posting only.
- Status: DOCUMENTATION_CHECKED
- Outstanding: Verify app review requirements, product configuration, user
  experience requirements, media restrictions, quotas and actual application access.

### Google Ads — OAuth

- Source: https://developers.google.com/google-ads/api/docs/oauth/overview
- Checked on: 2026-10-12
- Finding: Google Ads API uses OAuth 2.0 and requires a developer token.
  OAuth credentials and the API access level must be configured appropriately.
- Scope: Authentication prerequisites only.
- Status: DOCUMENTATION_CHECKED
- Outstanding: Verify access level, account access, quotas, permissions and the
  selected customer-account workflow.

### Shopify — API versioning

- Source: https://shopify.dev/docs/api/usage/versioning
- Checked on: 2026-10-12
- Finding: Shopify documents a quarterly API version schedule and recommends
  explicitly targeting a supported stable version. Versioned APIs and
  unversioned surfaces do not necessarily share the same lifecycle.
- Related source: https://shopify.dev/docs/api/admin-rest/usage/versioning
- Additional finding: REST Admin API is marked legacy; new integrations should
  evaluate GraphQL Admin API instead.
- Scope: API versioning and initial API selection only.
- Status: DOCUMENTATION_CHECKED
- Outstanding: Select the exact Shopify API surface and use case, confirm
  current version support, required scopes and access model.

## Verification limitations

DOCUMENTATION_CHECKED means a specific official page was inspected for the
limited finding recorded above. It does not mean that the provider integration
is implemented, approved, accessible or validated. Keep capability statuses
separate until their acceptance evidence is complete.
