# Erdős Problem 887 Lean formalization

This repository contains the Lean 4 companion formalization for Jarek Koch's manuscript:

**The Eventual Four-Divisor Bound for Erdős Problem 887: Root-band Reconstruction and a K5 Interval-Overload Obstruction**

Paper DOI: `10.5281/zenodo.20651083`
All-versions paper DOI: `10.5281/zenodo.20651082`

Archived Lean release DOI: `10.5281/zenodo.20586442`

## Project purpose

The manuscript proves an eventual four-divisor bound for Erdős Problem 887. For each fixed constant `C > 0`, it proves that there is a threshold `N(C)` such that the interval

```text
(sqrt(n), sqrt(n) + C n^(1/4))
```

contains at most four divisors of `n` for all `n >= N(C)`.

This repository contains the companion Lean 4 formalization. The paper is self-contained as a mathematical manuscript. The Lean development is a separate machine-checkable presentation of the same public theorem route.

The formalization mirrors the paper's theorem-source architecture. It includes the external reconstruction route, the bounded full `K5` survivor funnel, the canonical interval-overload construction, and the internal obstruction closure.

## Main files

* `Erdos887/Formalization.lean`
  Main Lean formalization.

* `Erdos887.lean`
  Root import file.

* `lakefile.toml`
  Lake project configuration.

* `lean-toolchain`
  Lean toolchain version.

## Checking the formalization

From the repository root, run:

```bash
lake build
```

The repository root is the directory containing `lakefile.toml` and `lean-toolchain`.

## Lean version

The Lean version is specified in:

```text
lean-toolchain
```

## Main formal endpoint

The principal public endpoint is:

```lean
Erdos887Formal.Paper_Corollary_1_2_Final
```

Related theorem-surface declarations include:

```lean
Erdos887Formal.Paper_Theorem_1_1_Final
Erdos887Formal.canonicalOverloadReconstruction_of_externalExtraction
```

## Artifact links

Manuscript preprint:

```text
https://doi.org/10.5281/zenodo.20651083
```

All manuscript versions:

```text
https://doi.org/10.5281/zenodo.20651082
```

Archived Lean release:

```text
https://doi.org/10.5281/zenodo.20586442
```

GitHub repository:

```text
https://github.com/jarekkoch-hub/erdos887-lean
```

## Citation

```text
Koch, J. (2026). The Eventual Four-Divisor Bound for Erdős Problem 887: Root-band Reconstruction and a K5 Interval-Overload Obstruction. Zenodo. https://doi.org/10.5281/zenodo.20651083
```

## Notes for readers

This repository is intended as an audit companion to the manuscript. The Lean file is organized to mirror the paper's reduction chain rather than to serve as a minimal mathlib-style formalization.

The central route is:

```text
external infinite five-divisor violations
→ root-band survivor reconstruction
→ bounded full K5 survivor funnel
→ canonical interval-overload datum
→ internal obstruction
→ contradiction
```

The manuscript explains the mathematical meaning of the source components and retained-state handoffs. The Lean file provides the corresponding machine-checkable theorem surface.
