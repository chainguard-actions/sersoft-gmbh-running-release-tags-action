<!-- markdownlint-disable -->

# Hardening Report: sersoft-gmbh--running-release-tags-action/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **sersoft-gmbh--running-release-tags-action/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The composite action references `actions/setup-node@v3`, which is a mutable tag rather than a pinned 40-character commit SHA. This means the action could silently pull in changed or malicious code if the tag is moved. It should be pinned to a full SHA, e.g. `actions/setup-node@1a4442cacd436585916779262731d1f68b8d2664 # v3`.

Locations:

- `.github/actions/generate-action-code/action.yml:7`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/setup-node@v3` to its full commit SHA `3235b876344d2a9aa001b8d1453c930bba69e610` in `.github/actions/generate-action-code/action.yml`, preserving the tag as a comment (`# v3`) for readability.

