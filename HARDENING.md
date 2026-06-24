<!-- markdownlint-disable -->

# Hardening Report: sersoft-gmbh--running-release-tags-action/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **sersoft-gmbh--running-release-tags-action/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The composite action at .github/actions/generate-action-code/action.yml uses `actions/setup-node@v3`, which is pinned to a mutable tag rather than an immutable 40-character commit SHA. This exposes the action to supply-chain attacks if the tag is moved to point to a different (potentially malicious) commit.

Locations:

- `.github/actions/generate-action-code/action.yml:6`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/setup-node@v3` to its full commit SHA `3235b876344d2a9aa001b8d1453c930bba69e610` in `.github/actions/generate-action-code/action.yml`. The original tag `v3` is preserved as a comment for readability.

