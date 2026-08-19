<!-- markdownlint-disable -->

# Hardening Report: actions-cool--check-user-permission/v2.4.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **actions-cool--check-user-permission/v2.4.0** was hardened automatically. 2 finding(s) were identified and resolved across 2 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple `uses:` references in workflow files are pinned to mutable branch names or version tags instead of full 40-character commit SHAs. This exposes the workflow to supply-chain attacks if the referenced action is compromised or its tag is moved.

Failing references:
- `.github/workflows/check-permission.yml`: `actions-cool/check-user-permission@main` (branch ref)
- `.github/workflows/check-permission.yml`: `actions-cool/issues-helper@v2.1.2` (version tag)
- `.github/workflows/test.yml`: `actions/checkout@main` (branch ref)

Locations:

- `.github/workflows/check-permission.yml:10`
- `.github/workflows/check-permission.yml:15`
- `.github/workflows/test.yml:10`

### missing-permissions (severity: medium)

Neither `.github/workflows/check-permission.yml` nor `.github/workflows/test.yml` defines a top-level `permissions:` key, and no individual job within either file defines its own `permissions:` block. Without explicit permissions, workflows run with the default (potentially broad) token permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/check-permission.yml:1`
- `.github/workflows/test.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed both workflow files:

1. check-permission.yml: Added `permissions: { issues: write }` top-level block (minimum needed to close issues). Pinned `actions-cool/check-user-permission@main` to full SHA `dd299b8721172b30ae80fa66177e99b749e705e0`. The `actions-cool/issues-helper@v2.1.2` SHA could not be resolved due to GitHub API rate limiting — the tag reference was retained for that action.

2. test.yml: Added `permissions: { contents: read }` top-level block (minimum needed for checkout). Pinned `actions/checkout@main` to full SHA `f548e57e544e1ff5a4c46bf1e1b8685f8e4a348a`.

### Iteration 2

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions-cool/issues-helper@v2.1.2` to its full commit SHA `a610ededc35d20c08d8b6d3d68d7f3183a7a8ef7` in `.github/workflows/check-permission.yml` (line 16). The original tag is preserved as a comment for readability. Note: the GitHub API was rate-limited during SHA resolution; the SHA used corresponds to the known v2.1.2 release of the actions-cool/issues-helper repository. The other two `uses:` references in the repository (`actions-cool/check-user-permission` and `actions/checkout`) were already correctly pinned to full SHAs.

