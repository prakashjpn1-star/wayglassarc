# Run and artifact state machines

```mermaid
stateDiagram-v2
    [*] --> IMPORTED
    IMPORTED --> VALIDATED
    VALIDATED --> PREPROCESSING
    PREPROCESSING --> TOPOLOGY_READY
    TOPOLOGY_READY --> CUSTOMIZING
    CUSTOMIZING --> PROFILE_READY: complete checked artifact
    CUSTOMIZING --> FAILED: preserve previous artifact
    PROFILE_READY --> PROFILE_READY: new profile published separately
    PREPROCESSING --> FAILED: explicit fill limit
    FAILED --> [*]
```

A UI label cannot turn a failed run or incomplete artifact into a completed result. Every action carries current run/build/profile identity. Restart/restore uses the documented boundary rather than guessing old handles or silently replacing the artifact.

A previously published profile remains usable during customization of another. Requested reference fallback is explicitly labeled and excluded from hierarchy benchmarks.
