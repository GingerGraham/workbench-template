# Changelog

All notable changes to `__MODULE_REPO__` are documented here.

## [Unreleased]

### Added

- **`tests/check-no-bare-alias.sh` guard (workbench-core D124).** Fails on
  a bare `alias name=...` in `bin/`, `lib/`, `bootstrap.sh`, `shell/` or
  `hooks/` (whichever the module has). Define aliases with
  `workbench_alias_define <name> <module> <value>`, which leaves an alias or
  function the user already has alone; a trailing `# wb-allow-bare-alias`
  comment allows a line on purpose. The default `core_api` floor is now
  `>=1.10 <2.0`, the version that provides the helper. Modules generated
  from this template inherit both.
- **`tests/check-no-bare-cd.sh` guard (workbench-core D110).** Fails on a
  bare `cd` or `ls` in `bin/`, `lib/`, `bootstrap.sh`, `shell/` or `hooks/`
  (whichever the module has); write `builtin cd` and
  `command ls`, since a host profile's aliases and functions would
  otherwise run inside sourced module code. A trailing `# wb-allow-bare`
  comment allows a line on purpose. Modules generated from this template
  inherit the guard.
- **Manual `workflow_dispatch` release override.** `release.yml` now
  accepts a `bump_type` (patch/minor/major) input to force a release
  through `workbench-core`'s reusable `module-release.yml`, regardless of
  what Conventional Commits since the last tag would compute — a floor,
  never a downgrade of a higher severity already pending. Manual dispatch
  only runs from `main`. See `workbench-core`'s `docs/decisions-log.md` D67.
- **`.github/dependabot.yml`** — weekly `github-actions` updates, so the
  pinned core workflow tags and the `actions/checkout` SHA stay current.

### Changed

- **Bug report template asks for OS family and environment separately.**
  The single "Platform" dropdown is replaced by an "Operating system"
  dropdown (Fedora/RHEL, Debian/Ubuntu, Arch, SUSE, other Linux, macOS),
  an optional distribution and version field, and an "Environment"
  dropdown (directly on the OS, container, or WSL2), so a report says
  which distro it ran on and whether that was WSL2 or a container.
- **Core workflows pinned to a core release tag (workbench-core D78).**
  `ci.yml`, `pr-check.yml`, `release.yml` and `release-finalize.yml` call
  `module-*.yml@v2.21.1` instead of `@main`, and `core_ref` now defaults to
  core's latest release (D40) instead of `main`. Every workflow declares
  `permissions: contents: read` (the bootstrap job keeps `contents: write`),
  and `actions/checkout` is SHA-pinned to the same v7.0.1 commit core uses.
  The placeholders and placeholder-guard steps are unchanged.
- **`workbench.yml` `core_api` is `">=1.8 <2.0"`** — 1.8 is the floor for
  core-generated getters (D89).
- **Agent and contributor guidance covers the stale-base CHANGELOG trap
  (workbench-core D115).** `AGENTS.md`, `.github/copilot-instructions.md`,
  `CONTRIBUTING.md`, the PR template and the conventional-commits skill
  checklist now say to check, before opening a PR and before any later
  push, that a release which landed on `main` since you branched hasn't
  left your `[Unreleased]` entry inside the released section, and to look
  at the Release run after merging. Modules generated from this template
  inherit it.
