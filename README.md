# Erdős Problem 887 Lean formalization

This repository contains a Lean 4 companion formalization for Jarek Koch's paper on Erdős Problem 887.

The paper is self-contained. The Lean development is a separate machine-checkable formalization of the same public theorem route.

## Contents

- `Erdos887/Formalization.lean`: main Lean formalization.
- `Erdos887.lean`: root import file.
- `lakefile.toml`: Lake project configuration.
- `lean-toolchain`: Lean toolchain version.

## Checking the formalization

From the repository root, run:

```bash
lake build
```

The repository root is the directory containing `lakefile.toml` and `lean-toolchain`.

## Lean version

The Lean version is specified in `lean-toolchain`.

## Archive

The public release of this repository is intended to be archived through Zenodo.