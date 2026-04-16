# Cloud GSA Prototype (v0.2)

A minimal session-and-telemetry runtime for the **1:3:1(+M)** framework:

- **1** = MKS(Conservation)+ (foundation)
- **3** = KitchenLab / Robot EDU / WalkWise-SQM+ (domains)
- **1** = Cloud GSA (shared backend)
- **M** = Meta Organization Layer (governance)

This repository contains a hardened prototype that demonstrates a shared session lifecycle, telemetry ingestion, basic metric computation, and cross-domain retrieval using a single runtime pattern.

## Current Status

This is a **working prototype**, not a finished platform.

What it currently demonstrates:
- Session lifecycle (`start -> ingest -> metrics -> close -> retrieve`)
- Protocol-driven sample validation on ingest
- A common runtime across KitchenLab, Robot EDU, and WalkWise/SQM+
- Prototype-grade metric computation with Yellow-Pad-style interpretability
- FastAPI backend, client simulation, and integration test coverage

What it does **not** yet do:
- PostgreSQL-backed persistence in the running app
- Production-grade authentication and authorization
- Mature domain analytics for final SQM/gait scoring
- Full protocol registry enforcement and versioning

## Repository Contents

- `main.py` - FastAPI runtime and API endpoints
- `models.py` - core entities and type system
- `metrics.py` - prototype metric computations and registry metadata
- `edge_sim.py` - simulated edge-device telemetry generator
- `session_client.py` - minimal client-side session runner and plotting helper
- `test_integration.py` - end-to-end API test coverage
- `schema.sql` - PostgreSQL seed schema and enum/table definitions
- `ARCHITECTURE.md` - architecture summary
- `ROADMAP.md` - staged development path

## Quick Start

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

Then in another terminal:

```bash
python edge_sim.py --domain kitchenlab
```

Or run the integration test:

```bash
python test_integration.py
```

## Design Intent

This project is meant to stay **small, intelligible, and honest**:
- low-friction runtime
- physically interpretable metrics
- common session grammar
- clear path from edge -> client -> cloud

The goal is to create a real seed runtime for a unified platform, not a vague architecture exercise.
