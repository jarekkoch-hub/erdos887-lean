# Erdős Problem 887: Lean formalization rewrite

> **Status: unfinished research checkpoint**  
> **Branch:** `formalization-rewrite`  
> **Current source:** [`Formalization3.lean`](Formalization3.lean)  
> **Snapshot date:** 16 October 2026

This branch records the current architectural rewrite of the Lean 4 companion formalization for Jarek Koch's manuscript:

**The Eventual Four-Divisor Bound for Erdős Problem 887: Root-band Reconstruction and a K5 Interval-Overload Obstruction**

The manuscript presents a proposed proof that, for each fixed `C > 0`, the interval

```text
(sqrt(n), sqrt(n) + C n^(1/4))
```

contains at most four divisors of `n` for all sufficiently large `n`.

**The end-to-end Lean formalization remains incomplete. This snapshot does not announce completed formal verification of the proposed result.**

## Current development

The current rewrite is approximately 42,000 source lines, including executable mathematics, architectural metadata, guidance systems, and scaffolding for unfinished stages. The line count describes the size of the development, not a measure of proof completion.

The manuscript mirrors the formalization's original architecture. This branch contains the subsequent rewrite, with more explicit control over mathematical states, construction ownership, and retained-state handoffs.

The source tracks the external reconstruction, canonical interval-overload construction, and internal obstruction routes. Later sections include scaffolding and unresolved mathematical producers. The source's opening guidance and closing construction-status ledger describe how the development is organized and where work remains.

## What changed

The rewrite makes the execution architecture explicit through:

- Nested containers, layers, proof boxes, and route compartments.
- Designated public state-transformation theorems with incoming state, outgoing state, and effect descriptions.
- Typed input/output roles for construction, retained reads, source inputs, coherence, permissions, and distant dependencies.
- Direct handoffs that preserve the selected witness and shared objects across constructions.
- Separate treatment of exact finite states, sequence states, subsequences, and normalized growth states.
- Explicit distinctions between closed routes, local diagnostics, and source-dependent intermediate compositions.
- A ledger identifying the remaining construction obligations.

## Development context and current limitation

I have developed this project independently with LLM assistance. Progress on the current strategy has stalled at the practical memory and structural limits of the LLM tools I have used.

Continuing the proof requires a coherent picture of nested mathematical states, branch history, provenance, and dependencies across distant stages. In my sessions, models lose their position within that nesting, follow shared internal references in circles, or confuse the boundaries between states.

Reconstructing the architecture for each fresh session now consumes so much usable context that the session can reach its practical limit before meaningful progress resumes. Extensive guidance embedded in the Lean source has not removed this bottleneck. Maintaining continuity between sessions has remained a manual responsibility.

This snapshot is published as a dated record of the work, its current construction frontier, and the technological limitations encountered with this strategy.

## Files and historical material

| File | Role |
| --- | --- |
| `Formalization3.lean` | Current unfinished rewrite checkpoint. |
| `Erdos887/Formalization.lean` | Earlier public formalization, retained for historical comparison. |
| `Erdos887.lean` and `Main.lean` | Project entry files inherited from the earlier development. |
| `Lean_Audit.tsv` | Audit map for the earlier public formalization; it is not an updated map of this rewrite. |
| `lakefile.toml`, `lake-manifest.json`, and `lean-toolchain` | Existing project configuration and dependency information. |
| `CITATION.cff` | Citation metadata inherited from the earlier public development. |

## Build and verification status

The previous README records a successful local build for **v1.1.0**:

```text
lake build
Build completed successfully (7663 jobs).
```

That is a historical build record for the earlier release. This README does not report a new build result for `Formalization3.lean`.

A build of the inherited project targets should only be described as checking the rewrite when `Formalization3.lean` is explicitly included in that build. The rewrite's build coverage and end-to-end theorem completion are separate matters.

For the earlier endpoint declarations, audit-surface update, mirror layer, and original build instructions, consult the [v1.1.0 README](https://github.com/jarekkoch-hub/erdos887-lean/blob/v1.1.0/README.md).

## Manuscript and archived releases

- [Manuscript preprint](https://doi.org/10.5281/zenodo.20651083)
- [All manuscript versions](https://doi.org/10.5281/zenodo.20651082)
- [Archived Lean release v1.1.0](https://doi.org/10.5281/zenodo.20693472)
- [Archived Lean release v1.0.0](https://doi.org/10.5281/zenodo.20586442)
- [All archived Lean versions](https://doi.org/10.5281/zenodo.20586441)
- [GitHub release v1.1.0](https://github.com/jarekkoch-hub/erdos887-lean/releases/tag/v1.1.0)

The version-specific Lean DOIs above identify the earlier archived releases. They should not be used as identifiers for the current rewrite checkpoint.

## Citation

For the manuscript:

```text
Koch, J. (2026). The Eventual Four-Divisor Bound for Erdős Problem 887:
Root-band Reconstruction and a K5 Interval-Overload Obstruction.
Zenodo. https://doi.org/10.5281/zenodo.20651083
```

For an earlier archived formalization, cite the DOI of the specific release used. For this research checkpoint, identify the repository, commit or release tag, `Formalization3.lean`, and snapshot date so readers can locate the exact version.
