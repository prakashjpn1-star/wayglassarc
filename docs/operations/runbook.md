# Offline setup operation and artifact recovery

The reference stack is: C++20 with checked 64-bit costs, standard containers/binary artifact I/O, a permitted local HTTP adapter, and HTML/CSS/JavaScript with SVG or Canvas 2D. Exact dependencies require environment inventory.

Inventory the actual permitted compiler/runtime and mirror before pinning versions; record license notices and offline build/test commands. Runtime CLIs are implementation deliverables, not existing executable engines in this documentation baseline. Headless tests must not require a browser or sound/GPU path.

Keep source, generated fixtures, runtime staging and immutable evidence in separate directories. Format changes reject incompatible artifacts clearly. Before selecting new artifacts, complete/verify them and preserve a valid previous selection. Restore into an isolated run/project directory rather than silently editing current state.

Restore verifies network/topology/profile/customization hashes and witness structure. Queries remain pinned to one complete artifact pair, and reference fallback must be requested/labeled.

Back up immutable inputs/artifacts/manifests and raw reports together with checksums. A checkpoint/snapshot cannot recover later changes absent from it. Cleanup preserves active artifacts and failure evidence. Process-stop recovery claims do not imply arbitrary power-loss or corrupted-disk recovery.
