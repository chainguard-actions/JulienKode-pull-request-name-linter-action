<!-- markdownlint-disable -->

# Hardening Report: JulienKode--pull-request-name-linter-action/v20.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **JulienKode--pull-request-name-linter-action/v20.5.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Both workflow files reference GitHub Actions using mutable version tags (e.g. @v6) instead of pinned 40-character commit SHA digests. This exposes the workflow to supply-chain attacks where a tag could be moved to point to malicious code. Failing references in build.yml: actions/checkout@v6, pnpm/action-setup@v6, actions/setup-node@v6. Failing references in test.yml: actions/checkout@v6, pnpm/action-setup@v6, actions/setup-node@v6.

Locations:

- `.github/workflows/build.yml:13`
- `.github/workflows/build.yml:14`
- `.github/workflows/build.yml:15`
- `.github/workflows/test.yml:14`
- `.github/workflows/test.yml:15`
- `.github/workflows/test.yml:16`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable tag references in both .github/workflows/build.yml and .github/workflows/test.yml:
- actions/checkout@v6 → @d23441a48e516b6c34aea4fa41551a30e30af803 # v6
- pnpm/action-setup@v6 → @0ebf47130e4866e96fce0953f49152a61190b271 # v6
- actions/setup-node@v6 → @249970729cb0ef3589644e2896645e5dc5ba9c38 # v6
Original tags are preserved as inline comments for readability.

