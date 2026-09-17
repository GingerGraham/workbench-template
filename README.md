# __MODULE_REPO__

<!-- TODO: one-sentence description of what this module does. -->

An **ecosystem module** (`workbench-core` ARCHITECTURE.md §2) — meaningless
standalone. Requires `workbench-core` installed first:

```sh
wb add __MODULE_SHORT__
# or, as part of a bundle:
wb install --bundle <bundle-name>
```

## What this module does

<!-- TODO: numbered list of what this module actually installs/configures. -->

## What this module does NOT do

<!-- TODO: explicit non-goals, and anything intentionally left to the
     machine owner or to another module. -->

## Shell functions

<!-- TODO: if this module registers shell content (register.shell[] in
     workbench.yml), document the functions/aliases it adds here. -->

## Requires

<!-- TODO: any binaries this module assumes are already installed. -->

---

## Using this template

This repo is a GitHub template — generate a new repo from it (the "Use
this template" button, or `gh repo create --template
GingerGraham/workbench-template`) rather than `git clone`-ing it
directly. Only "Use this template" generation produces a fresh repo with
no shared git history, which is what fires the `push` event
`.github/workflows/template-bootstrap.yml` listens for.

On the new repo's first push, that workflow substitutes
`__MODULE_REPO__`/`__MODULE_SHORT__` throughout the tree, commits the
result, and deletes itself — no manual step required. **Do this before**
applying the standard module branch ruleset (mirroring the other
`workbench-*` repos) to the new repo: a freshly generated repo has no
ruleset yet, so the bootstrap workflow's direct push to `main` works;
once a ruleset blocking direct pushes is in place, it won't.

Everything in this template ships unconditionally, including `hooks/` —
delete what your module doesn't need rather than the reverse. This
section, and the rest of this README below the divider above, only
makes sense in the template itself — replace it with your module's own
documentation once bootstrap has run.
