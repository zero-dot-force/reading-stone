# Spec Delta

## MODIFIED Requirements

### Requirement: Package scaffold and entry point

> Previously: version `0.2.0`.

The system SHALL provide a `reading-stone` package installable via `npm ci`, with `package.json` declaring name `reading-stone`, version `0.2.1`, `type: module`, `engines.node >=22`, license `Apache-2.0`, two `bin` entries — `reading-stone` and `gaze-analyzer-typescript` (Gaze's tier-3 PATH discovery name) — both pointing to `dist/main.js`, an `exports` map exposing `"."` (types `dist/index.d.ts`, default `dist/index.js`) and `"./package.json"`, and exactly one runtime dependency: `typescript` pinned exactly at `7.0.2` (the runtime consumes the `typescript/unstable/*` surface, which carries no semver stability guarantee). `src/index.ts` SHALL expose `export const VERSION = "0.2.1"`.

#### Scenario: Package metadata is correct

- **WHEN** `package.json` is inspected
- **THEN** name is `reading-stone`, version is `0.2.1`, `type` is `module`, `engines.node` is `>=22`, license is `Apache-2.0`, `bin` is exactly `{ "reading-stone": "dist/main.js", "gaze-analyzer-typescript": "dist/main.js" }`, and `dependencies` is exactly `{ "typescript": "7.0.2" }`

#### Scenario: Version constant is exposed

- **WHEN** the package entry is imported
- **THEN** `VERSION` equals `"0.2.1"`
