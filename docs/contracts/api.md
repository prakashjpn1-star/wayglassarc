# API contract

The local API validates bounded input, pins exact run/artifact identity and distinguishes domain failures from infrastructure faults.

## Local APIs and artifacts

Suggested operations: generate/import network, validate topology, preprocess hierarchy, create/customize profile, inspect artifact, query route, compute reachable set, compare against reference, run benchmark, and retrieve report.

Suggested routes are `POST /networks`, `POST /networks/{id}/preprocess`, `POST /profiles`, `POST /profiles/{id}/customize`, `POST /routes`, `POST /reachable`, `GET /artifacts/{id}`, and `GET /reports/{id}`. Each response includes immutable input identity and execution mode.

Bound request size, profile count, queued queries, reachable-set size, route length, artifact bytes, and inspection pages. A route beyond a response limit returns an explicit limit result or a paginated artifact with total cost; it is never silently truncated. Distinguish invalid input, no route, unavailable profile, incompatible artifact, resource limit, and internal error.

The service binds to loopback. File import operates on synthetic local files. No map provider, location permission, network tile request, or external process control is required.

## Concrete companion contracts

[JSON Schemas](../../schemas/README.md), [worked examples](../../examples/README.md) and [artifact formats](../../formats/README.md) define proposed shapes. Validation errors are 400/422, missing targets 404, stale identity/revision 409, excessive bytes 413 and resource/unavailable conditions explicit 429/503 or typed domain errors as appropriate. Responses carry stable code/message, correlation ID and exact run/artifact identity. Numerical, NO_ROUTE, compile rejection, guest trap and internal fault remain distinct domain outcomes, not flattened into generic success. Default inspection pages are 50, maximum 200 unless a stricter domain limit applies.
