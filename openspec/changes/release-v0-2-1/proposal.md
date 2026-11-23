# Proposal

## Why

v0.2.0 was published by hand. The dispatched `release` workflow (`add-release-workflow`) has merged but has never completed a run: its first dispatch, with tag `v0.2.1`, stopped at the Verify job because `package.json` on `main` still declares `0.2.0`. A patch release is the smallest change that exercises the whole pipeline end to end: the preflight creates the tag, the `npm` environment gates the job, `npm stage publish` goes through trusted publishing, and a maintainer approves the staged version.

## What Changes

- Version `0.2.0` → `0.2.1`: `package.json`, `package-lock.json`, `VERSION` in `src/index.ts`, the README status heading, and the `tests/cli.test.ts` metadata pins.
- `CHANGELOG.md`: a dated `0.2.1` entry noting that the package code is identical to 0.2.0 and that this is the first release made by the `release` workflow, with npm provenance.

Out of scope: any runtime, protocol, or packaging change.

## Capabilities

### New Capabilities

None.

### Modified Capabilities

- `cli`: the `Package scaffold and entry point` requirement moves to version `0.2.1`.

## Impact

- `package.json`, `package-lock.json`, `src/index.ts` (`VERSION` only), `tests/cli.test.ts`, `README.md`, `CHANGELOG.md`.
- `openspec/specs/cli/spec.md` via this change's delta.
- No runtime behavior change; no dependency change. The Gaze protocol contract is unchanged (v1.2.0); `initialize` does not report the package version.

## Constitution Alignment

- **I. Protocol Fidelity — PASS**: no protocol change.
- **II. Detection Accuracy — N/A**: no detection code changes.
- **III. TypeScript-Native Analysis — N/A**: no analysis code changes.
- **IV. Testability — PASS**: the existing `package metadata` tests pin the new version; the 85% gate is unchanged.
- **V. Analysis Safety — PASS**: no new dependencies.
