# Accuracy resources and performance requirements

These pass bars are required targets, not measured results. Accuracy, resource and performance evidence use frozen fixtures/settings.

## Synthetic generator and fixture families

Generate reproducible networks with grids, radial roads, ring roads, express connectors, cul-de-sacs, one-way corridors, bridge crossings, disconnected districts, and parallel alternatives. Use deterministic coordinate and cost generation from a recorded seed.

Include at least three profiles: base, peak-cost redistribution, and closure scenario. Every profile remains a static metric snapshot. Turn restrictions include forbidden left turns, U-turn policy, and direction-dependent penalties. Do not build every benchmark from an unrestricted uniform grid.

The mandatory large graph contains 50,000 intersections and approximately 150,000 directed segments. After turn expansion, cap the accepted fixture at 200,000 states and 600,000 transitions. Record actual counts; generate a reproducible fixture within those bounds. One-million-intersection experiments are stretch results only.

Small hand-calculated fixtures cover cases that a large random test may miss. For graphs with at most 30 routing states, compare with an additional all-pairs dynamic-programming oracle, including unreachable and equal-cost alternatives.

## Workload and performance pass bars

| Dimension | Proposed required target |
| --- | --- |
| Exactness campaign | 10,000 seeded point-to-point pairs across the mandatory graph and profiles; exact reference cost equality and independent legal-path checks |
| Small graphs | At least 200 generated small graphs checked against the all-pairs oracle |
| Topology preprocessing | Complete mandatory graph within 10 minutes and 2 GiB combined application memory |
| Full customization | Each required profile within 10 seconds on the mandatory graph |
| Query load | At least 100 completed accelerated routes/second for 60 measured seconds, using 32 logical clients and at most 16 simultaneous HTTP connections |
| End-to-end latency | p95 at most 500 ms including client queueing, path unpacking, and bounded response serialization |
| Algorithmic speedup | At least 3x median core search-time improvement over the independent Dijkstra baseline on 1,000 predeclared long-distance pairs |
| Reproducibility | Same-build repeated preprocessing/customization yields matching artifact digests |
| Soak | 30 minutes of mixed queries and profile publication without mixed-profile paths or unbounded retained artifacts |

The load mix is 60% cross-district pairs, 20% local pairs, 10% closure-affected pairs, and 10% disconnected pairs. The graph and pair corpus are frozen before tuning. Do not substitute only neighboring intersections to inflate throughput.

These are proposed thresholds, not results. Record machine/runtime, language, build, graph sizes, hierarchy arcs, triangle work, profile digests, warm-up, five repetitions, errors, percentiles, memory, and distance-only versus full-path timing. The baseline must be a competent priority-queue Dijkstra, not an intentionally slow implementation. Report any missed bar and revise openly before acceptance.
