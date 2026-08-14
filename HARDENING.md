<!-- markdownlint-disable -->

# Hardening Report: JulienKode--pull-request-name-linter-action/v0.4.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **JulienKode--pull-request-name-linter-action/v0.4.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference `actions/checkout@v1`, which is a mutable tag rather than a pinned 40-character commit SHA. If the tag is moved (e.g. by a compromised upstream), the workflow will silently execute different code. Pin to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v1`.

Locations:

- `.github/workflows/build.yml:9`
- `.github/workflows/test.yml:10`

### missing-permissions (severity: medium)

Neither workflow file declares a top-level `permissions:` block, and no job within them declares job-level permissions. Without explicit permissions, GitHub Actions grants the default (potentially write) token permissions, violating the principle of least privilege. Add a top-level `permissions: {}` or specific minimal scopes (e.g. `contents: read`) to each workflow.

Locations:

- `.github/workflows/build.yml:1`
- `.github/workflows/test.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed both workflow files (.github/workflows/build.yml and .github/workflows/test.yml):
1. Pinned `actions/checkout@v1` to the full commit SHA `50fbc622fc4ef5163becd7fab6573eac35f8462e` with a `# v1` comment for readability.
2. Added `permissions: {}` at the top level of each workflow to enforce least-privilege token access.

