# Acceptance and oracle plan

Independent oracles and preserved counterexamples establish correctness. Every acceptance item starts NOT RUN.

## Correctness, metamorphic tests, and interruption cases

Compare every sampled route cost with the independent raw-road router. Recalculate path cost from original segment IDs, verify every adjacency/turn, and check endpoint identity. For tied paths, accept different legal paths with equal optimal cost.

Metamorphic checks: increasing one road's cost cannot lower the optimal cost; removing a restriction cannot worsen it; closing a road absent from an existing optimal route leaves that route available and its optimal cost unchanged; splitting a road into two compatible segments with identical total cost and preserved endpoint turn rules preserves relevant distances between original intersections; translating/rotating geometry leaves costs unchanged.

Interrupt artifact creation before publication, during checksum generation, and before response. Loading a truncated or mismatched artifact must fail clearly. Run queries while another profile is customized and verify that every response uses one complete profile. Keep all failed seeds and concrete counterexample paths.

## Acceptance catalog

All items begin **NOT RUN**.

| ID | Required evidence |
| --- | --- |
| WA-01 | Import rejects malformed costs, endpoints, and turn rules |
| WA-02 | One-way, parallel-road, bridge, and disconnected fixtures route correctly |
| WA-03 | Turn expansion agrees with the independent raw-road state model |
| WA-04 | Source/target boundary costs and zero-length/no-route semantics pass |
| WA-05 | All 200 small graphs match the independent all-pairs oracle |
| WA-06 | Hierarchy preserves exact costs across 10,000 mandatory query/profile cases |
| WA-07 | Every unpacked route is legal and recomputes to the reported cost |
| WA-08 | Directed asymmetry and early-stop counterexamples pass |
| WA-09 | Closure/customization changes affect all required shortcuts correctly |
| WA-10 | In-flight queries never mix topology/profile artifacts |
| WA-11 | Hidden reference fallback is absent from accelerated benchmark traffic |
| WA-12 | Reachable sets match independent turn-aware budget searches |
| WA-13 | Metamorphic cost/restriction/geometry checks pass |
| WA-14 | Corrupt, incomplete, or mismatched artifacts fail explicitly |
| WA-15 | Same-build deterministic artifact digests match |
| WA-16 | Mandatory preprocessing, customization, query, memory, and speedup bars pass |
| WA-17 | Soak has zero incorrect routes and bounded queues/artifact retention |
| WA-18 | Browser tests cover profile changes, illegal turns, route explanation, and no-route cases |
| WA-19 | Full offline run succeeds without tiles, accounts, GPU features, or internet |
| WA-20 | Reproduction command rebuilds fixtures, oracle comparisons, and raw evidence |
