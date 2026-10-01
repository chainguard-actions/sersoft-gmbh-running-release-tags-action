<!-- markdownlint-disable -->

# Hardening Report: sersoft-gmbh--running-release-tags-action/v4.0.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **sersoft-gmbh--running-release-tags-action/v4.0.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The composite action at `.github/actions/generate-action-code/action.yml` references `actions/setup-node@v6`, which is a mutable tag reference rather than a pinned 40-character commit SHA. This means the action could silently change if the upstream tag is moved, enabling a supply-chain attack. It should be pinned to a full SHA, e.g. `actions/setup-node@<40-char-sha> # v6`.

Locations:

- `.github/actions/generate-action-code/action.yml:7`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/setup-node@v6` to `actions/setup-node@249970729cb0ef3589644e2896645e5dc5ba9c38 # v6` in `.github/actions/generate-action-code/action.yml`. The mutable tag reference was replaced with the full 40-character commit SHA to prevent supply-chain attacks from tag movement.

