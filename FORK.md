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

## Upstream engagement (deferred)

Do **not** open issues or PRs against `mschauer/CausalInference.jl` until:

1. DAGMakie 0.1.1 (viz-only + CausalInference weakdep) is released / stable
2. CausalDynamics façades over CausalInference pass CI and book smoke checks
3. Fork deltas in `FORK.md` are reviewed as worth upstreaming

Track candidate upstream items in this file only.

## Local use

```julia
# From CDCS root
using Pkg
Pkg.develop(path="packages/CausalInference.jl")
```

Or via `[sources.CausalInference]` in the CDCS `Project.toml`.
