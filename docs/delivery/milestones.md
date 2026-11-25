# Delivery and release gate

Deliver runnable slices with actual evidence and explicit remaining failures; required quantitative bars remain intact.

## Session plan

1. Freeze road/turn/cost semantics, small fixtures, and local dependency choices.
2. Build importer, synthetic generator, and independent raw-road Dijkstra.
3. Implement turn expansion, source/target handling, and all-pairs small-graph checks.
4. Build topology ordering and hierarchy structure; validate shortcut preservation.
5. Implement full metric customization and directional witnesses.
6. Implement accelerated queries, stopping conditions, and path unpacking.
7. Add closure profiles, immutable query selection, artifact recovery, and reachable sets.
8. Build browser map, turn explanations, and oracle comparison views.
9. Run large exactness campaign, speedup/load tests, and soak; retain counterexamples.
10. Finish offline packaging, benchmark evidence, limitations, and acceptance review.

Each session ends with runnable commands, measured results, known failures, and a next checkpoint. This is multi-day work; the program's separate rules govern individual session duration.

## Language, desktop fit, and deliverables



Use local Chrome with bundled HTML/CSS/JS. TypeScript is optional if its compiler is available in the provided mirror. Check dependencies before implementation and preserve their licenses. No apt-get or unavailable modules should be assumed.

Deliver source, graph/profile/artifact specifications, generator, reference router, hierarchy code, query core, unpacker, UI, CLI/API instructions, fixed benchmark manifest, raw comparisons, failure cases, and acceptance matrix. Distinguish actual measurements from future scale goals.

## Risks and future expansion

Primary risks are incorrect turn-state boundaries, shortcut direction mistakes, unsound termination, hierarchy fill growth, and stale metric witnesses. Exact reference comparisons take priority over a faster-looking demo. The synthetic graph generator must contain enough hierarchy and restrictions to exercise these risks honestly.

Future work can explore better separator ordering, genuinely incremental customization, time-dependent profiles, alternative routes, or larger public licensed maps. None is counted as complete or required to prove the first release. The required system is already substantial because topology, turn semantics, metric customization, accelerated search, and path reconstruction must all agree.
