# Product requirements

Find an exact legal route through fictional roads, restrictions and closures, then explain its original segments and costs. Acceleration must preserve legality and one immutable traffic profile throughout the query.

## Purpose

Build an offline routing engine that finds exact shortest legal routes through a large synthetic road network, including one-way streets, prohibited turns, turn penalties, closures, and changing travel-cost profiles. It must accelerate queries with its own hierarchical graph algorithms, reconstruct real road segments from shortcuts, and explain each result in a local browser map.

The intended users are engineers interested in geographic algorithms and developers building routing tools. The hard problem is making the accelerated answer remain exactly correct when a superficially shorter path contains an illegal turn or uses shortcut costs computed for another traffic profile. A line drawn across a map is not enough: its legality and total cost must be independently checkable.

This is geographic graph-algorithm work. It does not extend earlier workflow, messaging, reservation, gateway, synchronization, consensus, streaming, or database-index projects. Its core is shortest-path computation and turn-aware hierarchy construction, not service traffic routing or index migration.

## End state

Deliver a synthetic road-network generator, validated graph importer, turn-aware graph model, independent reference router, topology preprocessing, metric customization, accelerated exact query engine, shortcut unpacker, reachable-area analysis, browser map, CLI/API, correctness campaign, and benchmark report.

Implement the routing core. An existing routing service, GIS package, graph-routing library, or precomputed route dataset cannot provide the actual answers. Standard libraries may supply JSON, containers, HTTP, sorting, and basic drawing.

The release is complete when routes are exact and legal across the mandatory fixtures and load campaigns, hierarchy speedup is measured against a reference, and metric changes cannot silently mix incompatible costs.

## Required scope and exclusions

Required: directed roads; parallel segments; disconnected components; explicit turn restrictions/costs; exact nonnegative integer-cost routing; path reconstruction; hierarchical acceleration; at least three cost profiles; closure updates; immutable per-query profile selection; route explanation; travel-budget reachable sets; and offline map inspection.

Deferred: real GPS, online traffic ingestion, real-world addresses/geocoding, transit schedules, fleet assignment, vehicle routing with many stops, arbitrary topology changes without preprocessing, continuous time-dependent travel functions, and continent-scale capacity claims.

Travel costs are fixed for the whole query. A new profile represents a different snapshot of conditions. The engine does not model changing traffic while a vehicle is already traveling. This explicit boundary keeps exactness testable.
