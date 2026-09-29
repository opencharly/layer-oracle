# AGENTS.md — layer-oracle

Standalone candy repo for the `oracle` layer — the Oracle CLI for bundling
prompts and running multi-engine AI queries, installed globally via npm. The
candy lives in `charly.yml` at the repo root: the `require:` on `layer-nodejs`,
the `plan:` checks, and the embedded `skill:` entity projected into the
marketplace corpus as `/charly-coder:oracle`.

Canonical files:

- `charly.yml` — the `oracle:` candy entity and the `oracle-skill:` skill entity.
- `package.json` — the npm package spec for `@steipete/oracle`.
- `CHANGELOG/` — per-CalVer release history.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-coder:oracle` — the owning skill. Prompt bundling and multi-engine AI
  queries. Load before editing or troubleshooting.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, the `require:`/`package.json` install
  pattern, and service declarations). Load before editing any entity field or
  plan step.

## Build / validate / test

- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- The candy's `plan:` `check:` steps assert the binary lands at the fixed path
  and `oracle --version` exits cleanly — verifiable with no network access.

## Modify this repo

- Edit the `oracle:` candy entity AND the `oracle-skill:` skill entity in
  `charly.yml` together. The skill is the projected usage source.
- A version change goes in `package.json`; keep the `require:` on `nodejs` and
  the fixed binary path in step with the package's install layout.
- New behaviour claims belong in the `plan:` as an observable `check:` step, and
  in the skill body.

## Landing

- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo — read it
  before landing.
- Release history lives in `CHANGELOG/`.
