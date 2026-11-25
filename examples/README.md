# Worked examples

These small fictional inputs and hand-calculated oracles illustrate the contracts. They are not completed benchmark or acceptance results. All counts, identities and expectations depend on the described isolated setup.

| Example | Schema | Interpretation |
| --- | --- | --- |
| [turn-diamond.json](turn-diamond.json) | [network](../schemas/network.schema.json) | The 200 ms geometric/direct path is illegal. Base legal A-to-C route is ad,dc at 280 ms. |
| [base-profile.json](base-profile.json) | [profile](../schemas/profile.schema.json) | Empty overrides inherit the frozen network metric. Actual artifact binding uses content digests. |
| [relaxed-profile.json](relaxed-profile.json) | [profile](../schemas/profile.schema.json) | The physical turn existed in topology even while prohibited. Full customization permits the 200 ms route. |
| [closure-profile.json](closure-profile.json) | [profile](../schemas/profile.schema.json) | A-to-C is now unreachable: the other path retains its forbidden turn. |
| [route-request.json](route-request.json) | [route-request](../schemas/route-request.schema.json) | Requires a complete customized artifact. No hidden reference fallback is permitted. |
| [base-route-oracle.json](base-route-oracle.json) | [route-oracle](../schemas/route-oracle.schema.json) | Hand-calculated total: 140 + 0 turn penalty + 140. |
| [no-route-oracle.json](no-route-oracle.json) | [route-oracle](../schemas/route-oracle.schema.json) | Different from A-to-A, which is OK with cost 0 and an empty segment list. |
| [reachable-request.json](reachable-request.json) | [reachable-request](../schemas/reachable-request.schema.json) | Exact reachable intersections are A at 0, B at 100 and D at 140; C at 280 is excluded. |

The turn diamond distinguishes a legal optimal path, zero-cost empty route and NO_ROUTE. Full runtime campaigns add parallel roads, asymmetric costs, bridges and disconnected components.

Real fixture generators, actual checksum manifests, mandatory large campaigns and raw results remain implementation deliverables. Counterexamples and failed runs must be retained rather than replaced with successful-looking templates.
