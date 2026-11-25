# Diagnostics and measurement

```mermaid
flowchart TD
    Core["Core algorithms"] --> D["Bounded state and diagnostics"]
    Fixture["Frozen seed and configuration"] --> R["Raw reproducible report"]
    D --> UI["Browser inspection"]
    D --> R
    Oracle["Independent correctness oracle"] --> R
```

Record original/expanded/fill sizes, triangle work, artifact hashes, query mode, settled states, relaxed arcs, search/unpack/serialization time and complete legal-path cost differences.

Include hardware/runtime/build, seed, precision/overflow policy, complete fixture and five repetitions where specified. Keep complete latency distributions and failed/incomplete runs. Profiling does not replace the oracle; a faster incorrect answer is a failure. Benchmark verification/GC/core work is timed according to the required workload, not silently excluded.
