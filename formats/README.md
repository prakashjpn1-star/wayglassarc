# Graph profile hierarchy and witness formats

## Identity and costs

Network/profile JSON follows the [schemas](../schemas/README.md). Profile overrides inherit the frozen network defaults; every omitted/duplicate/unknown target has explicit validation semantics. Default U-turn permission is declared, with explicit pair overrides taking precedence. Topology includes all physically connected turn pairs regardless of current permission.

Finite internal cost is checked signed 64-bit. INF is INT64_MAX/4; a finite operation reaching/exceeding INF returns COST_OVERFLOW instead of becoming a cheap/saturated result. Inputs fit bounded JSON integers; totals/sentinel-facing diagnostics serialize as decimal strings or tagged UNAVAILABLE, never ambiguous floating point.

## Topology binary

Proposed format magic WATP, little-endian u32 version, section-count/table with u64 offsets/lengths, network digest, state-to-original-segment table, rank/order, directed physical transitions, complete fill skeleton and checksums. Validate lengths, references, rank permutation and caps before allocation/publication.

## Customized binary

Magic WAMC, version, topology digest and exact profile digest, per-direction finite/unavailable weights, witness table and SHA-256. Witness is ORIGINAL(transitionId) or VIA(lowerRankState,leftWitness,rightWitness). Dependencies must form a verified acyclic decomposition; ties cannot point to self. A lower-rank dependency proof/check is part of the selected CCH implementation.

## Query boundary

Forward seeds are source outgoing-segment costs; reverse targets are states ending at destination with zero remaining cost. Empty source=target returns zero before search. Unpack yields original segments and exact legal turns. One pinned complete artifact pair covers search, witnesses and final explanation.

## Publication and retention

Build into staging, validate every section/hash, then atomically select the complete immutable artifact. Interrupted customization cannot change prior queries. Reference-counted query pins block deletion. Explicit response/work/resource limits produce errors or complete paginated artifacts, never silent truncated paths.
