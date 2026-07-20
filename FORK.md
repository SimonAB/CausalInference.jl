# SimonAB fork of CausalInference.jl

Upstream: https://github.com/mschauer/CausalInference.jl  
Fork: https://github.com/SimonAB/CausalInference.jl  

Used by the CDCS book stack (`DAGMakie.jl`, `CausalDynamics.jl`) as the dagitty-like identification layer.

## Policy

- Develop interop helpers and CDCS-driven fixes **here first**.
- Do **not** open upstream issues or PRs until DAGMakie + CausalDynamics + this fork form a coherent, tested stack.
- Keep the upstream package UUID (`8e462317-f959-576b-b3c1-403f26cec956`) so CDCS can path-develop this checkout while General still resolves the same name/UUID.

## CDCS-driven deltas vs upstream

(Track commits below as they land.)

- *None yet — fork tip matches upstream `0.19.3` at creation.*

## Local use

```julia
# From CDCS root
using Pkg
Pkg.develop(path="packages/CausalInference.jl")
```

Or via `[sources.CausalInference]` in the CDCS `Project.toml`.
