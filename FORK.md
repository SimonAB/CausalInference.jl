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

Do **not** open issues or PRs against `mschauer/CausalInference.jl` until all gates below are green:

1. **DAGMakie 0.1.1** (viz-only + CausalInference weakdep) — tagged and Registrator submitted (2026-07-23); wait for General AutoMerge.
2. **CausalDynamics 0.1.0** façades over CausalInference — tagged and Registrator submitted (2026-07-23); CI / book smoke still required after AutoMerge.
3. Fork deltas in this file reviewed as worth upstreaming (especially GraphMakie `"0.5, 0.6"` — required before DAGMakie 0.1.1 and CausalDynamics can share a single registry test env with GraphMakie 0.6).

Track candidate upstream items in this file only.

## After both packages are on General

1. Open upstream PRs for the deltas above (GraphMakie compat first).
2. Re-enable `DAGMakieCausalDynamicsExt` in a DAGMakie patch release once CausalDynamics is on General (symmetric extension already lives on the CausalDynamics side).
3. Keep the CDCS **GraphMakie 0.6.3** pin and Makie 0.24.8 book pin unless explicitly approved to change.

## Local use

```julia
# From CDCS root
using Pkg
Pkg.develop(path="packages/CausalInference.jl")
```

Or via `[sources.CausalInference]` in the CDCS `Project.toml`.
