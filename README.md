# oracle

The Oracle CLI as a charly layer — a prompt-bundling tool that runs multi-engine
AI queries.

The `oracle` candy installs the `@steipete/oracle` npm package globally from its
`package.json`, placing the `oracle` executable on PATH at
`${HOME}/.npm-global/bin/oracle`. It requires the `nodejs` runtime. The binary's
presence and its `--version` entrypoint are deterministically verifiable in the
built image with no network access or API credentials.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `oracle` |
| Requires | `layer-nodejs` |
| Binary | `${HOME}/.npm-global/bin/oracle` |
| Service / port | none |

## How to use it

Compose the layer in a box's `candy:` list:

```yaml
my-box:
  candy:
    # the named box's value is the box BODY; `base:` and the `candy:` list are its keys
    base: fedora
    candy:
      - '@github.com/opencharly/layer-oracle:v2026.243.0409'
```

Then run it inside the container:

```bash
charly shell my-box -c "oracle --version"
```

## Layout

- `charly.yml` — the `oracle:` candy entity (the `require:` dep and the `plan:`
  checks) plus the embedded `skill:` entity.
- `package.json` — the npm package spec for `@steipete/oracle`.
- `CHANGELOG/` — per-CalVer release history.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-coder:oracle` — prompt bundling and multi-engine AI
  queries.
- Runtime dependency: `/charly-coder:nodejs`.
- Composed by: `/charly-openclaw:openclaw-full`.
- [`opencharly/opencharly](https://github.com/opencharly/opencharly) — the umbrella.
