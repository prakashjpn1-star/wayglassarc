# Architecture decisions

## ADR 1 Reference stack

C++20 with checked 64-bit costs, standard containers/binary artifact I/O, a permitted local HTTP adapter, and HTML/CSS/JavaScript with SVG or Canvas 2D. Exact dependencies require environment inventory.

The exact compiler/runtime version, HTTP/JSON/schema libraries and offline test tools remain subject to permitted-mirror inventory. No package or desktop performance is assumed verified. The source permits other host languages; this is the concrete reference direction to review.

## ADR 2 Core ownership

Turn-aware states distinguish incoming road direction. Topology preprocessing, full metric customization, exact search and shortcut unpacking are separate stages. No external map or routing library supplies answers.

Implement customizable contraction hierarchy topology, full directional customization and query/unpacking directly. A raw-road independent Dijkstra and small all-pairs oracle remain separate.

## ADR 3 Immutable identities and artifacts

Version scene/network/profile/source, configuration, artifact format and executable build. Use a declared SHA-256 digest over canonical inputs or versioned binary bytes. Reject nonfinite JSON/invalid encodings and corrupted artifacts. Immutability prevents a displayed run from silently using a different source/profile/scene.

## ADR 4 Deterministic limits

Stable IDs/order, seeded generators and frozen work limits are part of the contract. Reaching a cap returns explicit failed/incomplete/limit state. Never drop constraints, shortcuts, traps or source effects to meet a timing bar. Same-build reproducibility does not imply universal bitwise portability.

## ADR 5 Offline UI

Use semantic HTML, ordinary CSS and small JavaScript modules, with bounded tables and optional Canvas/SVG drawings. Software rendering remains supported where required. No tiles, CDN editors, fonts, telemetry, accounts or remote services are hidden prerequisites.

## Open evidence gates

Exact dependency pins, calibrated caps, format compatibility fixtures, independent oracle challenges, accuracy/cost/semantics campaigns and measured resources remain runtime milestones. These decisions make no programme or benchmark approval claim.
