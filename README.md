# Autonomous Discovery Engine

> **OCN Module** — Self-directed research and knowledge discovery system for the Omniscient Civilization Nexus (OCN).

[![CI](https://github.com/GALACTIC-UNION/autonomous-discovery-engine/actions/workflows/ci.yml/badge.svg)](https://github.com/GALACTIC-UNION/autonomous-discovery-engine/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)

---

## Overview

**Autonomous Discovery Engine (ADE)** conducts self-directed research across structured databases, scientific literature, and the open web. It harvests data, detects novel patterns, generates hypotheses, and validates them — all without requiring explicit human queries. Discoveries are automatically ingested into `knowledge-graph-universal` and surfaced to `cognitive-synthesis-framework` for strategic synthesis.

---

## Architecture

```
┌──────────────────────────────────────────────────────────┐
│               Autonomous Discovery Engine                 │
│                                                          │
│  ┌──────────────┐   ┌─────────────────┐                 │
│  │ DataHarvester│──▶│ PatternDiscovery│                 │
│  └──────────────┘   └────────┬────────┘                 │
│                              │                           │
│              ┌───────────────▼───────────────┐           │
│              │     HypothesisGenerator        │           │
│              └───────────────┬───────────────┘           │
│                              │                           │
│              ┌───────────────▼───────────────┐           │
│              │      ValidationEngine          │           │
│              └───────────────┬───────────────┘           │
│                              │                           │
│              ┌───────────────▼───────────────┐           │
│              │       DiscoveryPublisher       │           │
│              │   (→ KGU + CSF + Education)    │           │
│              └───────────────────────────────┘           │
└──────────────────────────────────────────────────────────┘
```

---

## Modules

| Module | Path | Responsibility |
|--------|------|----------------|
| **DataHarvester** | `src/harvester/` | Crawls scientific databases, APIs, and literature sources; normalizes raw data |
| **PatternDiscovery** | `src/patterns/` | Statistical and structural pattern detection across harvested datasets |
| **HypothesisGenerator** | `src/hypothesis/` | Generates testable hypotheses from detected patterns using abductive reasoning |
| **ValidationEngine** | `src/validation/` | Tests hypotheses against existing knowledge and new data; assigns confidence scores |
| **DiscoveryPublisher** | `src/publisher/` | Routes validated discoveries to KGU, CSF, and the Personalized Education Matrix |
| **SchedulerDaemon** | `src/scheduler/` | Manages autonomous discovery cycles, priority queues, and rate limiting |

---

## API Surface

Base URL: `https://api.ocn.galactic-union.io/ade/v1`

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/discover` | Trigger a targeted discovery run on a domain or question |
| `GET`  | `/discoveries` | List recent validated discoveries |
| `GET`  | `/discoveries/{id}` | Get a specific discovery with evidence trail |
| `POST` | `/hypothesize` | Generate hypotheses from provided data |
| `POST` | `/validate` | Validate a hypothesis against the knowledge base |
| `GET`  | `/scheduler/status` | Current autonomous discovery cycle status |
| `POST` | `/scheduler/trigger` | Manually trigger a discovery cycle |
| `GET`  | `/health` | Health and readiness check |

---

## Directory Structure

```
autonomous-discovery-engine/
├── src/
│   ├── harvester/     # DataHarvester
│   ├── patterns/      # PatternDiscovery
│   ├── hypothesis/    # HypothesisGenerator
│   ├── validation/    # ValidationEngine
│   ├── publisher/     # DiscoveryPublisher
│   └── scheduler/     # SchedulerDaemon
├── docs/
│   ├── index.md
│   ├── api.md
│   └── discovery-cycle.md
├── tests/
│   ├── unit/
│   ├── integration/
│   └── fixtures/
├── config/
│   ├── default.yaml
│   └── sources.yaml   # Data source registry
├── .github/workflows/ci.yml
├── CONTRIBUTING.md
└── README.md
```

---

## Getting Started

```bash
git clone https://github.com/GALACTIC-UNION/autonomous-discovery-engine.git
cd autonomous-discovery-engine
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp config/default.yaml config/local.yaml
pytest tests/ -v --cov=src
```

---

## License

MIT © GALACTIC-UNION / KOSASIH
