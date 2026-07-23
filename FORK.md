# SimonAB fork of CausalInference.jl

Upstream: https://github.com/mschauer/CausalInference.jl  
Fork: https://github.com/SimonAB/CausalInference.jl  

Used by the CDCS book stack (`DAGMakie.jl`, `CausalDynamics.jl`) as the dagitty-like identification layer.

## Policy

- Develop interop helpers and CDCS-driven fixes **here first**.
- Do **not** open upstream issues or PRs until DAGMakie + CausalDynamics + this fork form a coherent, tested stack.
- Keep the upstream package UUID (`8e462317-f959-576b-b3c1-403f26cec956`) so CDCS can path-develop this checkout while General still resolves the same name/UUID.

## CDCS-driven deltas vs upstream

- Widen `[compat] GraphMakie` to `"0.5, 0.6"` so CDCS can resolve the local GraphMakie 0.6.3 fork alongside CausalInference as a DAGMakie test extra.
- `sorted_union_` accepts `AbstractVector` (not only `Vector`) so Zig-Zag / PDAG helpers work with Graphs ≥1.14 `FrozenVector` neighbour views.

## Upstream engagement (gates)

Candidate PRs opened against `mschauer/CausalInference.jl` (2026-07-23):

- [#178](https://github.com/mschauer/CausalInference.jl/pull/178) — `sorted_union_` → `AbstractVector` (Graphs ≥1.14 `FrozenVector`)
- [#179](https://github.com/mschauer/CausalInference.jl/pull/179) — GraphMakie weakdep compat `"0.5, 0.6"`

Further fork-only work should still wait until DAGMakie 0.1.1 and CausalDynamics are on General and the CDCS stack has been smoke-tested.

## After both packages are on General

1. Land / follow up the PRs above (GraphMakie compat first for registry co-install with DAGMakie 0.1.1).
2. Re-enable `DAGMakieCausalDynamicsExt` in a DAGMakie patch release once CausalDynamics is on General (symmetric extension already lives on the CausalDynamics side).
3. Keep the CDCS **GraphMakie 0.6.3** pin and Makie 0.24.8 book pin unless explicitly approved to change.

## Local use

```julia
# From CDCS root
using Pkg
Pkg.develop(path="packages/CausalInference.jl")
```

Or via `[sources.CausalInference]` in the CDCS `Project.toml`.
