# Changelog

All notable changes to `__MODULE_REPO__` are documented here.

## [Unreleased]

### Added

- **Manual `workflow_dispatch` release override.** `release.yml` now
  accepts a `bump_type` (patch/minor/major) input to force a release
  through `workbench-core`'s reusable `module-release.yml`, regardless of
  what Conventional Commits since the last tag would compute — a floor,
  never a downgrade of a higher severity already pending. Manual dispatch
  only runs from `main`. See `workbench-core`'s `docs/decisions-log.md` D67.
- **`.github/dependabot.yml`** — weekly `github-actions` updates, so the
  pinned core workflow tags and the `actions/checkout` SHA stay current.

### Changed

- **Core workflows pinned to a core release tag (workbench-core D78).**
  `ci.yml`, `pr-check.yml`, `release.yml` and `release-finalize.yml` call
  `module-*.yml@v2.21.1` instead of `@main`, and `core_ref` now defaults to
  core's latest release (D40) instead of `main`. Every workflow declares
  `permissions: contents: read` (the bootstrap job keeps `contents: write`),
  and `actions/checkout` is SHA-pinned to the same v7.0.1 commit core uses.
  The placeholders and placeholder-guard steps are unchanged.
- **`workbench.yml` `core_api` is `">=1.8 <2.0"`** — 1.8 is the floor for
  core-generated getters (D89).
