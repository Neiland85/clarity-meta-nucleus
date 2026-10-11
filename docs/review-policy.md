# Review Policy

## Purpose

This policy defines repository ownership, review expectations, and the
limitations of the current single-maintainer operating model.

## Code ownership

The root `CODEOWNERS` file identifies `@Neiland85` as the default repository
maintainer for all paths unless more specific ownership rules are introduced.

Code ownership identifies responsibility. It does not prove that a change
has been independently reviewed, tested, or approved.

When additional maintainers join the repository, ownership should be split
by area according to demonstrated responsibility and repository permissions.

## Pull request expectations

Every change targeting `main` must use a pull request and satisfy the active
required status checks.

Pull requests should describe:

- Motivation, scope, and affected areas.
- Implementation and validation evidence.
- Security, permissions, data-handling, and compatibility risks.
- Known limitations and follow-up work.

Authors must not describe a check as passed unless its result has been
observed. Documentation-only changes should state when automated tests are
not applicable.

## Independent review

The current repository operates with a single known maintainer.
A maintainer must not treat their own authorship or CODEOWNERS match as
independent approval.

The current GitHub ruleset does not require an approving review or a code
owner review. This is intentional until an independent reviewer and a
workable approval policy are established.

Changes involving authentication, credentials, permissions, sensitive data,
security controls, or material changes to required CI checks should receive
independent review before merge whenever possible. If no independent reviewer
is available, defer high-risk changes rather than representing them as
independently reviewed.

## Enabling mandatory approvals

Before enabling mandatory review requirements:

1. Confirm that at least one eligible independent reviewer has repository
   access and can submit an approving review.
2. Define the approval count and whether code owner approval is required.
3. Confirm how changes authored by code owners will be reviewed.
4. Update the GitHub ruleset in a separate, auditable governance change.
5. Verify the effective ruleset and test the resulting pull request workflow.

Do not configure an approval requirement that the available reviewers cannot
satisfy.

## Evidence and status

Review, CI, and validation are separate forms of evidence. A passing CI run
does not establish independent human review or compatibility with live Meta
APIs.

Use the repository's documented validation status vocabulary consistently.
