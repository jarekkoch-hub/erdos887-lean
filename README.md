# Erdős Problem 887 Lean formalization

This repository contains the Lean 4 companion formalization for Jarek Koch's manuscript:

**The Eventual Four-Divisor Bound for Erdős Problem 887: Root-band Reconstruction and a K5 Interval-Overload Obstruction**

Paper DOI: `10.5281/zenodo.20651083`
All-versions paper DOI: `10.5281/zenodo.20651082`
Archived Lean release DOI, v1.0.0: `10.5281/zenodo.20586442`
All-versions Lean DOI: `10.5281/zenodo.20586441`
Current GitHub release: `v1.1.0`

## Project purpose

The manuscript proves an eventual four-divisor bound for Erdős Problem 887. For each fixed constant `C > 0`, it proves that there is a threshold `N(C)` such that the interval

```text
(sqrt(n), sqrt(n) + C n^(1/4))
```

contains at most four divisors of `n` for all `n >= N(C)`.

This repository contains the companion Lean 4 formalization. The paper is self-contained as a mathematical manuscript. The Lean development is a separate machine-checkable presentation of the same public theorem route.

The formalization mirrors the paper's theorem-source architecture. It includes the external reconstruction route, the bounded full `K5` survivor funnel, the canonical interval-overload construction, the normalized legal `K5` survivor surface, and the internal obstruction closure.

## v1.1.0 audit-surface update

Release `v1.1.0` adds audit-surface hardening and a Formal Conjectures / DeepMind-facing mirror layer.

The core proof route remains the same. The update makes the theorem-source architecture easier to inspect by adding explicit Lean declarations showing that `ExternalReconstructionSource` is exactly the pair of its two component source packages:

```lean
Erdos887Formal.ExternalCanonicalExtraction.CanonicalExtractionSource
Erdos887Formal.ExternalCanonicalExtraction.RootBandSurvivorReconstructionSource
```

The release also adds an eta theorem for the external reconstruction wrapper, a floor/ceil divisor-window count matching the Formal Conjectures style, the eventual answer-4 theorem surface, the existential `K = 4` bound, the Rosenfeld lower construction, and an audit package collecting the DeepMind-style mirror outputs.

## Main files

* `Erdos887/Formalization.lean`
  Main Lean formalization.

* `Erdos887.lean`
  Root import file.

* `Main.lean`
  Project entry file.

* `Lean_Audit.tsv`
  Human-readable audit map for the formalization. GitHub renders this file as a table. It lists the main formal packages, fields, constructors, theorem surfaces, and paper-section anchors so readers can inspect the structure of the Lean development without spreadsheet software.

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

The `v1.1.0` update was checked locally with:

```text
lake build
Build completed successfully (7663 jobs).
```

## Lean version

The Lean version is specified in:

```text
lean-toolchain
```

## Main formal endpoints

The principal public endpoint is:

```lean
Erdos887Formal.Paper_Corollary_1_2_Final
```

Related theorem-surface declarations include:

```lean
Erdos887Formal.Paper_Theorem_1_1_Final
Erdos887Formal.ExternalCanonicalExtraction.ExternalReconstructionSource
Erdos887Formal.ExternalCanonicalExtraction.externalReconstructionSource_nonempty_iff_components
Erdos887Formal.ExternalCanonicalExtraction.externalReconstructionSource_eta
Erdos887Formal.ExternalCanonicalExtraction.canonicalOverloadReconstruction_of_externalExtraction
```

The `v1.1.0` Formal Conjectures / DeepMind-facing mirror layer includes:

```lean
Erdos887Formal.FormalConjecturesMirror.erdos887WindowCount
Erdos887Formal.FormalConjecturesMirror.erdos887WindowCount_eq_formalConjecturesStyle
Erdos887Formal.FormalConjecturesMirror.erdos_887_parts_i_answer_four
Erdos887Formal.FormalConjecturesMirror.erdos_887_parts_ii
Erdos887Formal.FormalConjecturesMirror.erdos_887_variants_rosenfeld_infinite
Erdos887Formal.FormalConjecturesMirror.erdos_887_variants_rosenfeld_4_paper_recurring_form
Erdos887Formal.FormalConjecturesMirror.DeepMind887AuditPackage
Erdos887Formal.FormalConjecturesMirror.deepMind887MirrorStatement_from_auditPackage
Erdos887Formal.FormalConjecturesMirror.deepMind_count_identity
```

## Human audit map

The file

```text
Lean_Audit.tsv
```

is provided as a navigation aid for reviewers and readers. It is a plain tab-separated table, so it can be viewed directly on GitHub, opened in spreadsheet software, or inspected as text.

The audit map is intended to show what is packaged inside the formalization: structures, theorem-source packages, retained-state records, fields, constructors, theorem surfaces, and their corresponding paper-section anchors. It is not a separate proof and does not replace Lean checking. The authoritative formal artifact remains:

```text
Erdos887/Formalization.lean
```

A suggested audit path is:

```text
1. Build the project with lake build.
2. Inspect the public endpoint declarations.
3. Inspect ExternalReconstructionSource and its two component packages.
4. Use Lean_Audit.tsv to locate the major theorem-source packages and handoff records.
5. Compare those packages with the corresponding sections of the manuscript.
6. Follow the final route from external reconstruction to the canonical interval-overload obstruction.
7. For the Formal Conjectures comparison, inspect the FormalConjecturesMirror namespace.
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

Archived Lean release, v1.0.0:

```text
https://doi.org/10.5281/zenodo.20586442
```

All Lean release versions:

```text
https://doi.org/10.5281/zenodo.20586441
```

GitHub repository:

```text
https://github.com/jarekkoch-hub/erdos887-lean
```

## Citation

```text
Koch, J. (2026). The Eventual Four-Divisor Bound for Erdős Problem 887: Root-band Reconstruction and a K5 Interval-Overload Obstruction. Zenodo. https://doi.org/10.5281/zenodo.20651083
```

For the Lean formalization archive, cite the relevant Zenodo Lean release DOI. The all-versions Lean DOI is:

```text
https://doi.org/10.5281/zenodo.20586441
```

## Notes for readers

This repository is intended as an audit companion to the manuscript. The Lean file is organized to mirror the paper's reduction chain rather than to serve as a minimal mathlib-style formalization.

The central route is:

```text
external infinite five-divisor violations
→ root-band survivor reconstruction
→ bounded full K5 survivor funnel
→ canonical interval-overload datum
→ normalized legal K5 survivor surface
→ internal obstruction
→ contradiction
```

The manuscript explains the mathematical meaning of the source components and retained-state handoffs. The Lean file provides the corresponding machine-checkable theorem surface. The audit map gives readers a compact way to navigate the formal package structure while keeping the Lean file itself as the source of truth.

The `v1.1.0` additions are audit-facing. They do not replace the existing proof route. Their purpose is to make the wrapper structure explicit, expose the component-package decomposition, and provide a direct Formal Conjectures / DeepMind-style comparison layer.
