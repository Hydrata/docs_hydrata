# Validation

Hydrata runs **unmodified ANUGA** — the same open-source solver developed by Geoscience Australia and the Australian National University. Every simulation on Hydrata produces identical results to running ANUGA locally.

## Validation Record

ANUGA has been validated against:

- **30+ benchmark problems** — laboratory flume experiments, field observations, analytical solutions
- **Peer-reviewed publications** — over 100 papers using ANUGA for flood, tsunami, and storm surge modeling
- **Government-grade applications** — used by Geoscience Australia for national tsunami risk assessments

## Benchmarks

| Benchmark | Description | Status |
|---|---|---|
| [Merewether](merewether.md) | Urban flood in Newcastle, NSW — validated against observed flood marks | Verified on Hydrata |
| ANUGA validation suite | 30+ standard benchmarks from the ANUGA repository | Passes (upstream CI) |

## Regulatory Acceptance

ANUGA is accepted by regulators in multiple jurisdictions. See [Regulatory Acceptance](regulatory-acceptance.md) for details by jurisdiction.

## How Hydrata Preserves Solver Integrity

1. **Unmodified ANUGA** — Hydrata does not fork or modify the ANUGA solver. We use `anuga_core` as a dependency.
2. **Deterministic execution** — same inputs produce same outputs on Hydrata cloud or local Python.
3. **Portable model files** — Hydrata's `scenario.json` format can be exported and run locally with `run_anuga`.
4. **Open-source toolchain** — `run_anuga` (MIT licence) handles the Hydrata-to-ANUGA translation. [View on GitHub](https://github.com/Hydrata/run_anuga).
