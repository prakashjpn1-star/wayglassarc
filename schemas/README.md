# JSON Schema catalog

These draft-2020-12 schemas describe proposed version 1 request/data shapes. They complement the [domain contracts](../docs/contracts/data-and-artifacts.md) and [artifact specifications](../formats/README.md), not a running product.

| Schema | Purpose |
| --- | --- |
| [network.schema.json](network.schema.json) | Synthetic directed road network |
| [profile.schema.json](profile.schema.json) | Immutable static cost profile |
| [route-request.schema.json](route-request.schema.json) | Pinned exact point-to-point query |
| [reachable-request.schema.json](reachable-request.schema.json) | Inclusive travel-budget reachable set |
| [artifact-manifest.schema.json](artifact-manifest.schema.json) | Topology and customized artifact identity |
| [route-oracle.schema.json](route-oracle.schema.json) | Small-graph hand-calculated route oracle |

Semantic core checks go beyond JSON structure: finite parser values, decoded byte limits, exact identities, geometry/convexity, graph connectivity, cost overflow, type/effect legality or run state are checked by the relevant importer/service. Proposed array/string/work maxima are explicit design defaults pending target-environment verification. No real tokens or fabricated fixture hashes appear in examples.

These projects use versioned artifacts and owned memory. A database schema is not forced onto numerical arrays, graph preprocessing or a VM heap. The [format notes](../formats/README.md) specify those structures instead.
