<!-- markdownlint-disable -->

# Hardening Report: sersoft-gmbh--running-release-tags-action/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **sersoft-gmbh--running-release-tags-action/v3.0.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files and the composite action use `uses:` references pinned to mutable tags or branches instead of immutable 40-character commit SHAs, making them vulnerable to supply-chain attacks.

- `.github/workflows/codeql-analysis.yml`: `actions/checkout@v4`, `github/codeql-action/init@v2`, `github/codeql-action/autobuild@v2`, `github/codeql-action/analyze@v2`
- `.github/workflows/deploy.yml`: `actions/checkout@v4`
- `.github/workflows/tests.yml`: `actions/checkout@v4`, `sersoft-gmbh/running-release-tags-action@main`
- `.github/workflows/tag-update.yml`: `actions/checkout@v4`
- `.github/actions/generate-action-code/action.yml`: `actions/setup-node@v3`

Locations:

- `.github/workflows/codeql-analysis.yml:25`
- `.github/workflows/codeql-analysis.yml:28`
- `.github/workflows/codeql-analysis.yml:35`
- `.github/workflows/codeql-analysis.yml:43`
- `.github/workflows/deploy.yml:11`
- `.github/workflows/tests.yml:24`
- `.github/workflows/tests.yml:26`
- `.github/workflows/tag-update.yml:11`
- `.github/actions/generate-action-code/action.yml:6`

### missing-permissions (severity: medium)

Three workflow files have no top-level `permissions:` block and no job-level `permissions:` block on any of their jobs. Without explicit permissions, the GITHUB_TOKEN is granted its default (potentially broad) permissions.

- `.github/workflows/deploy.yml`: single job `deploy-action-code` has no permissions.
- `.github/workflows/tests.yml`: jobs `test-defaults`, `test-customized`, `test-from-env`, and `test-invalid` all have no permissions.
- `.github/workflows/tag-update.yml`: single job `update-tags` has no permissions.

Locations:

- `.github/workflows/deploy.yml:1`
- `.github/workflows/tests.yml:1`
- `.github/workflows/tag-update.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Pinned all mutable action references to full commit SHAs: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, github/codeql-action/{init,autobuild,analyze}@v2 → @b8d3b6e8af63cde30bdc382c0bc28114f4346c88, actions/setup-node@v3 → @3235b876344d2a9aa001b8d1453c930bba69e610, sersoft-gmbh/running-release-tags-action@main → @bcc4e87a54d5f3303db706edacf6397f13355bc7. Added permissions blocks: deploy.yml and tag-update.yml got job-level 'contents: write' (needed for git push / tag updates); tests.yml got top-level 'contents: read'. The codeql-analysis.yml already had a job-level permissions block.

