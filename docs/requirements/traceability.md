# Requirement and acceptance traceability

Every source section is covered, including behavioral prose. Section 2 is retained as an external ownership/approval gate in the archive.

| Source section | Contract | Design |
| --- | --- | --- |
| 1. Purpose | [Read](../requirements/product.md) | Cross-component boundary |
| 2. Ownership and program status | [Archive](../source/README.md) | Cross-component boundary |
| 3. End state | [Read](../requirements/product.md) | Cross-component boundary |
| 4. Required scope and exclusions | [Read](../requirements/product.md) | Cross-component boundary |
| 5. Network and metric contracts | [Read](../requirements/software.md) | [Network import and checked cost semantics](../design/import.md) |
| 6. Exact route semantics | [Read](../requirements/software.md) | [Network import and checked cost semantics](../design/import.md) |
| 7. Turn-aware state expansion | [Read](../requirements/software.md) | [Turn-aware topology and boundary seeding](../design/expansion.md) |
| 8. Architecture | [Architecture](../architecture/high-level-design.md) | Cross-component boundary |
| 9. Mandatory hierarchy algorithm | [Read](../requirements/software.md) | [Deterministic elimination order and fill topology](../design/hierarchy.md) |
| 10. Customization and shortcut witnesses | [Read](../requirements/software.md) | [Full directional weights and witness construction](../design/customization.md) |
| 11. Accelerated query and fallback contract | [Read](../requirements/software.md) | [Exact upward search and stable query profiles](../design/queries.md) |
| 12. Reachable-area analysis | [Read](../requirements/software.md) | [Exact network reachability and immutable artifact lifetime](../design/reachable.md) |
| 13. Synthetic generator and fixture families | [Read](../requirements/quality-and-benchmarks.md) | Cross-component boundary |
| 14. Workload and performance pass bars | [Read](../requirements/quality-and-benchmarks.md) | Cross-component boundary |
| 15. Local APIs and artifacts | [Read](../contracts/data-and-artifacts.md) | [Exact network reachability and immutable artifact lifetime](../design/reachable.md) |
| 16. Browser map and analysis UI | [Read](../requirements/browser.md) | Cross-component boundary |
| 17. Correctness, metamorphic tests, and interruption cases | [Read](../testing/acceptance-plan.md) | [Shortcut unpacking and original-route explanation](../design/unpacking.md) |
| 18. Acceptance catalog | [Read](../testing/acceptance-plan.md) | Cross-component boundary |
| 19. Session plan | [Read](../delivery/milestones.md) | Cross-component boundary |
| 20. Language, desktop fit, and deliverables | [Read](../delivery/milestones.md) | Cross-component boundary |
| 21. Risks and future expansion | [Read](../delivery/milestones.md) | Cross-component boundary |
| 22. Primary technical references | [Read](../architecture/references.md) | Cross-component boundary |

## Acceptance oracles

| ID | Required evidence | Outcome |
| --- | --- | --- |
| WA-01 | Import rejects malformed costs, endpoints, and turn rules | NOT RUN |
| WA-02 | One-way, parallel-road, bridge, and disconnected fixtures route correctly | NOT RUN |
| WA-03 | Turn expansion agrees with the independent raw-road state model | NOT RUN |
| WA-04 | Source/target boundary costs and zero-length/no-route semantics pass | NOT RUN |
| WA-05 | All 200 small graphs match the independent all-pairs oracle | NOT RUN |
| WA-06 | Hierarchy preserves exact costs across 10,000 mandatory query/profile cases | NOT RUN |
| WA-07 | Every unpacked route is legal and recomputes to the reported cost | NOT RUN |
| WA-08 | Directed asymmetry and early-stop counterexamples pass | NOT RUN |
| WA-09 | Closure/customization changes affect all required shortcuts correctly | NOT RUN |
| WA-10 | In-flight queries never mix topology/profile artifacts | NOT RUN |
| WA-11 | Hidden reference fallback is absent from accelerated benchmark traffic | NOT RUN |
| WA-12 | Reachable sets match independent turn-aware budget searches | NOT RUN |
| WA-13 | Metamorphic cost/restriction/geometry checks pass | NOT RUN |
| WA-14 | Corrupt, incomplete, or mismatched artifacts fail explicitly | NOT RUN |
| WA-15 | Same-build deterministic artifact digests match | NOT RUN |
| WA-16 | Mandatory preprocessing, customization, query, memory, and speedup bars pass | NOT RUN |
| WA-17 | Soak has zero incorrect routes and bounded queues/artifact retention | NOT RUN |
| WA-18 | Browser tests cover profile changes, illegal turns, route explanation, and no-route cases | NOT RUN |
| WA-19 | Full offline run succeeds without tiles, accounts, GPU features, or internet | NOT RUN |
| WA-20 | Reproduction command rebuilds fixtures, oracle comparisons, and raw evidence | NOT RUN |
