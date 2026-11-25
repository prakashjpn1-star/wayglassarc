# Software and domain requirements

Turn-aware states distinguish incoming road direction. Topology preprocessing, full metric customization, exact search and shortcut unpacking are separate stages. No external map or routing library supplies answers.

## Network and metric contracts

| Entity | Required fields |
| --- | --- |
| Intersection | stable ID, synthetic planar coordinates |
| Directed segment | stable ID, from/to intersections, polyline, positive travel cost, optional class |
| Turn rule | incoming segment, outgoing segment, allowed/prohibited, nonnegative penalty |
| Topology artifact | input hash, ordering, expanded graph, hierarchy arcs, format version |
| Metric profile | ID/version, topology hash, segment costs, turn costs/closures, digest |
| Customized hierarchy | topology hash, exact profile digest, directional weights, witnesses |
| Route | profile/version, original segment sequence, total segment/turn costs, status |
| Report | seed, graph/profile digests, build, comparisons, errors, timings |

Travel costs are integer milliseconds from 1 to 1,000,000,000 per segment. Turn penalties range from zero to 1,000,000 ms. Checked 64-bit accumulation uses a documented infinity sentinel. Overflow returns an explicit error; it cannot produce a falsely cheap route.

Reject invalid endpoints, duplicate segment IDs, nonfinite coordinates, negative costs, malformed turn connectivity, and inconsistent profile/topology hashes. Parallel segments remain distinct. Geometry crossings do not create connections unless an intersection is explicitly present.

## Exact route semantics

The cost of a segment sequence is the first segment's travel cost plus, for each later segment, its travel cost and the penalty for entering it from the previous segment. Every consecutive pair must connect and have an allowed turn. A closed segment or prohibited turn makes that traversal unavailable.

The first segment has no incoming-turn penalty. A route from an intersection to itself is the empty zero-cost route. An unreachable destination returns `NO_ROUTE`, not an empty successful path. U-turns follow explicit policy/rules; never assume that returning to the previous intersection is automatically allowed.

Any minimum-cost legal route is acceptable. Stable input and configuration must select a reproducible route, but the accelerated and reference algorithms need not select the same path when several paths tie. Compare exact total cost and independent legality in that case. Do not require global lexicographic path minimality unless a separate algorithm implements it.

## Turn-aware state expansion

A search state represents arriving via a directed segment. The topology contains all physically connected incoming/outgoing turn pairs that profiles may permit, including pairs currently prohibited. A profile gives prohibited turns infinite cost and permitted turns the outgoing segment cost plus turn penalty. This distinguishes reaching an intersection from different directions and allows a restriction to be lifted without inventing a missing hierarchy transition. A newly introduced physical connection outside this topology requires preprocessing again.

For a source intersection, seed its outgoing segment states with their segment travel costs. For a destination, accept any state whose segment ends there. Equivalent virtual source/sink arcs are allowed if zero-cost handling and path reconstruction are correct. Preserve source/destination boundary semantics in all accelerated queries.

The independent reference router must operate directly on the original roads and `(intersection, incoming_segment)` states. It must not consume the engine's expanded graph, hierarchy, shortcuts, or witness data. This catches graph-expansion bugs as well as query bugs.

## Mandatory hierarchy algorithm

Implement a documented customizable contraction hierarchy or an equivalently exact metric-customizable hierarchy. For the intended design, derive an elimination order from topology, construct the shortcut/fill structure, and customize directional arc weights using the selected metric.

Use a deterministic topology ordering, with nested geometric partitioning plus explicit separator handling suitable for the synthetic networks. It must remain correct for nonplanar bridge edges and disconnected components even if ordering quality worsens. Record order quality, hierarchy size, preprocessing cost, and memory.

Implement the algorithm from reviewed pseudocode with proof obligations for shortcut preservation and query termination. A path through eliminated states must remain representable. If a preprocessing resource cap is exceeded, return `PREPROCESS_LIMIT`; do not omit necessary shortcuts and continue with an approximate answer.

Both forward and backward directional costs are required for directed roads. A convenient undirected representation cannot erase one-way restrictions.

## Customization and shortcut witnesses

Customization starts from original transition costs and computes the required hierarchy weights for one exact profile digest. Closures are unavailable/infinite transitions. A weight change can affect shortcuts far from the changed road; editing only that road's hierarchy arc is not sufficient.

For the first release, fully customize each new profile. Local incremental customization is deferred. Retain enough witness information to unpack every selected shortcut into legal original transitions. Witness dependencies must be acyclic under the algorithm's ordering.

Tie handling is deterministic. Expanded paths are checked against the original roads and the selected profile. Corrupt or cyclic witness references must be rejected rather than looping or returning truncated geometry.

Publish a profile's customized artifact only after structural validation completes. An interrupted customization leaves the prior artifact usable and the new profile unavailable or explicitly reference-only. The artifact format is versioned and checksummed.

## Accelerated query and fallback contract

Use the hierarchy's exact upward/bidirectional query procedure and a sound stopping condition. Track settled states, relaxed arcs, meeting state, and unpacking cost. Tests must challenge premature termination with asymmetric and disconnected cases.

Every query selects one immutable topology/profile pair at invocation and returns its identity. The entire distance search and unpacking use that pair. A newly published profile affects subsequent queries, not an in-flight route.

If a profile has not been customized, the API may offer an explicitly requested reference fallback. It must identify `REFERENCE` mode. Accelerated benchmark results cannot include hidden fallback queries or claim fallback throughput as hierarchy throughput.

## Reachable-area analysis

Given source, profile, and travel budget, compute the exact set of reachable intersections and minimum arrival cost using a turn-aware search. For the first release this may use the reference-style exact search rather than the accelerated point-to-point procedure.

The UI colors reachable intersections and roads with clear budget labels. It must not claim a mathematically exact geographic polygon between roads. Reachability is defined on the network. Test budget equality, prohibited turns, one-way return paths, and closures.

This feature exercises whole-region computation and makes routing restrictions visible without turning the project into a map-service wrapper.
