# Roadmap

This tracks near-term direction for `ledgerlens-core`. It complements, rather
than replaces, the per-feature docs under `docs/` and the cross-repo contracts
documented in the [README's "LedgerLens Organization" section](README.md#ledgerlens-organization).

## Now

- **Restore automated releases.** `.github/workflows/release-please.yml` was
  removed; `CHANGELOG.md` and the `pyproject.toml` version are currently
  bumped by hand. Reinstate release-please (or an equivalent) so tagging,
  changelog generation, and the GHCR image publish stay in sync automatically.
- **Triage the `.github/ISSUES/` backlog.** Several issues in that directory
  (SDKs, audit log, multi-tenant namespaces, API key management, chaos
  testing, GNN ring detection, temporal patterns, streaming, tracing) already
  appear implemented in the current tree (`sdk/`, `packages/`, `audit/`,
  `api/namespace.py`, `api/api_key_router.py`, `tests/chaos/`,
  `detection/gnn_ring_detector.py`, `detection/temporal_patterns.py`,
  `api/streaming_router.py`, `detection/tracing.py`). Close or update the
  stale ones so the backlog reflects real open work.

## Next

- **Close the `core` → `api` handoff.** README's "Open Integration Points"
  still lists this as unresolved: how `RiskScore` records produced by
  `run_pipeline.py` reach the API layer (direct DB write, message queue, or
  an ingestion endpoint) is not yet decided.
- **Order-book event ingestion.** Needed to unblock `round_trip_trade_frequency`
  and cancellation-rate features — see the TODOs in
  `detection/feature_engineering.py`.
- **Document `ledgerlens-data`'s schema/version contract** — where labelled
  training data lives and how `detection/model_training.py` should consume it.

## Later

- Expand the GNN ring detector and federated learning paths beyond their
  current scope (see `docs/gnn_ring_detection.md`, `docs/federated_learning.md`)
  as production usage surfaces gaps.

## How to use this file

When a roadmap item ships, move its CHANGELOG entry to a dated release
section and delete the line here. When new cross-repo work is identified,
add it here rather than letting it live only in a chat thread or PR
description.
