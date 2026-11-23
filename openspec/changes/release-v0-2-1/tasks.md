# Tasks

## 1. Versioning

- [ ] 1.1 Bump version to `0.2.1` in `package.json`/`package-lock.json` (`npm version 0.2.1 --no-git-tag-version`) and `VERSION` in `src/index.ts`; update the `tests/cli.test.ts` version pins and the README status heading

## 2. Documentation

- [ ] 2.1 `CHANGELOG.md`: dated `0.2.1` entry and compare links

## 3. Gates

- [ ] 3.1 Run the CI parity gates — `npx biome check src/ tests/`, `npm run build`, `npx vitest run --coverage` — all pass at ≥85%
