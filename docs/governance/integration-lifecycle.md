# Integration Lifecycle and Acceptance Criteria

## Lifecycle states

1. DISCOVERED
   A business use case and potential provider product have been identified.

2. PENDING
   Requirements, sources or feasibility questions remain unresolved.

3. DOCUMENTED
   Relevant official requirements and architectural constraints are recorded.

4. ACCESS_PENDING
   Required app review, account eligibility, scopes, credentials or provider
   approval has not been confirmed.

5. IMPLEMENTED
   Code implements a defined capability; acceptance evidence may still be incomplete.

6. VALIDATED
   Acceptance criteria have passed and evidence is recorded for the exact
   provider product, environment, API version and capability.

7. DEPRECATED
   The capability is being retired or replaced with a documented transition.

## Transition rules

- DISCOVERED -> PENDING or DOCUMENTED
- PENDING -> DOCUMENTED or remain PENDING
- DOCUMENTED -> ACCESS_PENDING or IMPLEMENTED when prerequisites are met
- ACCESS_PENDING -> IMPLEMENTED after required access is confirmed
- IMPLEMENTED -> VALIDATED only after all applicable acceptance criteria pass
- Any active state -> PENDING if a critical assumption is invalidated
- Active states -> DEPRECATED when retirement is approved

Different capabilities from the same provider may have different states.

## Minimum evidence for VALIDATED

- Named provider, API product, version and capability scope.
- Official source references and dates checked.
- Authentication and required permissions confirmed for the tested environment.
- Reproducible success and unauthorized/rejected-operation tests.
- Tests for malformed input and relevant provider errors.
- Rate-limit and retry behavior assessed where applicable.
- Idempotency and duplicate processing assessed for retried writes or events.
- Webhook signature and replay handling assessed if webhooks are used.
- No secrets in source, fixtures, logs or committed test artifacts.
- Relevant privacy and data-handling controls evidenced.
- CI results, limitations and outstanding risks recorded.
- Reviewer and validation date recorded.
- Production approval recorded separately when required.

## Evidence record template

- Capability identifier:
- Provider / API product:
- Environment:
- API version:
- Commit:
- Source register references:
- Permissions confirmed:
- Test command and result:
- Security/privacy review:
- Known limitations:
- Reviewer:
- Validation date:
- Production approval:
- Next review trigger:

## Revalidation triggers

Revalidate when the provider changes API versions, scopes, review status, quotas,
webhook behavior or deprecation policy; when implementation changes materially;
or when an incident or new use case changes the risk.
