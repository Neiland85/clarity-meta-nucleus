# Contributing to Clarity Meta Nucleus

## Principles

- Preserve an auditable history.
- Make the smallest coherent change.
- Never commit credentials, access tokens, private keys, or production data.
- Do not describe a capability as validated unless the validation evidence exists.
- Keep Meta-specific assumptions explicit and versioned.

## Branch naming

Use one of these prefixes:

- `feature/`: new capability.
- `fix/`: defect correction.
- `docs/`: documentation-only change.
- `test/`: test additions or corrections.
- `security/`: security controls or remediation.
- `chore/`: maintenance and repository governance.
- `hotfix/`: urgent production correction.

Use short, lowercase, hyphen-separated descriptions.

## Commit messages

Follow Conventional Commits:

`type(scope): concise imperative description`

Common types:

- `feat`: new capability.
- `fix`: defect correction.
- `docs`: documentation.
- `test`: tests.
- `build`: build or dependency tooling.
- `ci`: continuous integration.
- `refactor`: behavior-preserving restructuring.
- `security`: security-related change.
- `chore`: maintenance.

Example:

`docs(governance): define repository contribution policy`

## Pull requests

- Target `main`.
- Explain the motivation, scope, and impact.
- List tests and validation actually performed.
- Identify security, permission, data-handling, and compatibility implications.
- Link related issues when available.
- Do not claim a check passed unless its result was observed.
- Keep changes focused and reviewable.

## Validation status vocabulary

- `DOCUMENTED`: described in repository documentation.
- `IMPLEMENTED`: present in code.
- `TESTED`: exercised by recorded tests.
- `VALIDATED_AGAINST_META`: verified against the relevant Meta interface.
- `DEPLOYED`: deployed to a declared environment.

These states are not interchangeable. A successful local test does not establish live Meta API compatibility or production readiness.

## Releases and tags

Use Semantic Versioning for published releases when the project has a defined release baseline. Release tags must be annotated and must point to reviewed, committed history. Do not create release tags merely to label an initial repository scaffold.

## Security reporting

Do not publish credentials, exploitable client details, or sensitive evidence in issues or pull requests. Use an appropriate private reporting channel for sensitive findings.
