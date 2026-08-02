# Sandbox provider leaderboard

Run [`30691551759`](https://github.com/starslingdev/hpc-sandbox-benchmarks/actions/runs/30691551759) · commit [`6da0dce9d1c37fa2d45517f63c02591292075d20`](https://github.com/starslingdev/hpc-sandbox-benchmarks/commit/6da0dce9d1c37fa2d45517f63c02591292075d20) ·
dataset [`data/dataset/runs/30691551759.json`](data/dataset/runs/30691551759.json) · generated 2026-08-01T09:08:16.544Z

Requested target for every provider: **4 vCPU · 8 GiB RAM · 40 GB disk**. This run contains **358 metric records**
backed by **3690 retained trial observations**, across **46 metrics** and
**8 providers**; every emitted, catalogued metric has a ranked table below
(median across sandboxes), grouped by dimension with its headline first — some behind a disclosure triangle, none omitted.
Generated from the published Run dataset — do not edit by hand. Methodology:
[`docs/methodology.md`](docs/methodology.md).

**How to read:** value = median across sandboxes (one machine, one vote) · interval = cluster bootstrap,
labelled 95% but ≈77% actual coverage at 3 sandboxes (see methodology) · rows share a rank only
when statistically indistinguishable or tied on the median (see details below) · a coverage gap means unmeasured, never a score of zero.
CPU/RAM comparability uses observed vCPU and RAM (±10% RAM); disk is a workload-capacity gate
surfaced through coverage gaps, not part of the compute-match verdict.

**Document order:** the real-world developer workflows lead, because what a developer or a CI job
actually waits on is what this benchmark exists to measure. The synthetic microbenchmarks (`cpu`, `disk`, `memory`, `network`, `system`)
load one hardware axis in isolation — a real question, but a different one — so each is collapsed by
default; expand a section to read its tables.

**The `realworld` section is drawn, not tabulated.** One stacked chart per repo, each bar a
whole pipeline on one environment and each segment a task. Its per-task rankings — the medians,
intervals and trial counts every bar is built from — are still here, one triangle down: the charts
are what the section is FOR, and the tables are how you check them.

## Providers in this run

Each provider's isolation technology — the **declared** technology is authoritative; **detected**
is a best-effort in-sandbox probe that cannot separate every isolation type (a container and a
microVM can both read `kvm`; gVisor and a microVM can both read `unknown`), shown only as a
cross-check.

| Provider | Isolation (declared) | Detected |
| --- | --- | --- |
| Blaxel | microVM | vm |
| Daytona (VM) | microVM (Linux VM) | vm |
| E2B | Firecracker microVM | vm |
| Microsandbox Cloud | libkrun microVM (cloud) | vm |
| Modal (gVisor) | gVisor container | gvisor |
| Modal (VM) | microVM (VM runtime) | vm |
| Namespace | microVM (dedicated instance) | vm |
| Novita | microVM | vm |

_Not present in this run: Daytona (container), Microsandbox (local), Vercel Sandbox — registered providers that reported no data (not dispatched, or every cell was lost before reporting anything)._

## realworld

What a developer or a CI job actually waits on: each bar is one environment's whole pipeline
for that repo, segmented by task in execution order. The charts share one time scale, so a second is the same length in all of them.

<img src="docs/figures/realworld-better-auth.webp" width="960" alt="Better-Auth: 10 pipeline tasks across 8 environments, stacked by task and sorted fastest-first">

<img src="docs/figures/realworld-mastra.webp" width="960" alt="Mastra: 4 pipeline tasks across 8 environments, stacked by task and sorted fastest-first">

<img src="docs/figures/realworld-openclaw.webp" width="960" alt="OpenClaw: 5 pipeline tasks across 7 environments, 1 disclosed as incomplete, stacked by task and sorted fastest-first">

<details>
<summary><strong>Per-task rankings</strong> · 19 tasks, with medians, intervals and trial counts</summary>

### Mastra: cold install _(headline)_

Seconds · lower is better

_Blaxel and Daytona (VM) share the top on this metric (lower is better)._

| Rank | Provider | Mastra: cold install (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 38.86 | 37.55 – 40.76 | 12 | 12 | — |
| 1 | Daytona (VM) | 39.96 | 38.43 – 43.23 | 12 | 12 | tied |
| 3 | Novita | 48.14 | 43.39 – 59.96 | 12 | 12 | — |
| 3 | Modal (VM) | 52.91 | 46.03 – 55.32 | 12 | 12 | tied |
| 3 | Namespace | 54.84 | 48.68 – 57.62 | 12 | 12 | tied |
| 6 | Microsandbox Cloud | 58.31 | 56.93 – 61.66 | 12 | 12 | — |
| 7 | E2B | 66.28 | 64.77 – 67.26 | 12 | 12 | — |
| 8 | Modal (gVisor) | 94.88 | 93.44 – 98.66 | 12 | 12 | — |

### Better-Auth: build

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.2× higher (lower is better)._

| Rank | Provider | Better-Auth: build (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 46.48 | 45.93 – 46.93 | 12 | 12 | — |
| 2 | Daytona (VM) | 57.98 | 56.12 – 59.98 | 12 | 12 | — |
| 3 | Blaxel | 60.91 | 59.52 – 61.58 | 12 | 12 | — |
| 4 | Modal (VM) | 70.65 | 68.9 – 76.22 | 12 | 12 | — |
| 4 | Novita | 75.58 | 68.51 – 86.28 | 12 | 12 | tied |
| 4 | Microsandbox Cloud | 77.42 | 76.55 – 79.62 | 12 | 12 | tied |
| 7 | E2B | 94.97 | 92.57 – 96.32 | 12 | 12 | — |
| 8 | Modal (gVisor) | 135.1 | 133 – 137.5 | 12 | 12 | — |

### Better-Auth: cold install

Seconds · lower is better

_Blaxel leads on median (lower is better); see notes for how ranks are decided._

| Rank | Provider | Better-Auth: cold install (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 11.49 | 11.39 – 11.65 | 12 | 12 | — |
| 2 | Daytona (VM) | 11.85 | 11.56 – 13.41 | 12 | 12 | — |
| 3 | Novita | 15.09 | 14.05 – 19.41 | 12 | 12 | — |
| 3 | Microsandbox Cloud | 17.82 | 16.91 – 19.31 | 12 | 12 | tied |
| 5 | E2B | 18.93 | 18.59 – 19.11 | 12 | 12 | — |
| 5 | Modal (VM) | 19.13 | 18.64 – 23.18 | 12 | 12 | tied |
| 5 | Namespace | 24.84 | 18.44 – 25.88 | 12 | 12 | tied |
| 8 | Modal (gVisor) | 34.51 | 32.64 – 36.05 | 12 | 12 | — |

### Better-Auth: git clone

Seconds · lower is better

_Blaxel leads · Modal (VM) is ~1.8× higher (lower is better)._

| Rank | Provider | Better-Auth: git clone (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 0.5855 | 0.564 – 0.612 | 12 | 12 | — |
| 2 | Modal (VM) | 1.051 | 0.7185 – 1.131 | 12 | 12 | — |
| 3 | E2B | 1.329 | 1.284 – 1.381 | 12 | 12 | — |
| 3 | Daytona (VM) | 1.401 | 1.322 – 1.441 | 12 | 12 | tied |
| 3 | Namespace | 1.703 | 0.9115 – 1.937 | 12 | 12 | tied |
| 6 | Novita | 2.006 | 1.87 – 2.096 | 12 | 12 | — |
| 7 | Modal (gVisor) | 2.413 | 2.239 – 2.702 | 12 | 12 | — |
| 8 | Microsandbox Cloud | 30.69 | 18.6 – 34.93 | 12 | 12 | — |

### Better-Auth: lint (Biome)

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.1× higher (lower is better)._

| Rank | Provider | Better-Auth: lint (Biome) (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 2.673 | 2.611 – 2.688 | 12 | 12 | — |
| 2 | Daytona (VM) | 3.067 | 3.046 – 3.228 | 12 | 12 | — |
| 3 | Blaxel | 3.213 | 3.153 – 3.363 | 12 | 12 | — |
| 4 | Modal (VM) | 4.06 | 3.987 – 4.162 | 12 | 12 | — |
| 4 | Microsandbox Cloud | 4.087 | 4.01 – 4.351 | 12 | 12 | tied |
| 4 | Novita | 4.11 | 3.564 – 4.558 | 12 | 12 | tied |
| 7 | E2B | 5.127 | 5.048 – 5.171 | 12 | 12 | — |
| 8 | Modal (gVisor) | 10.55 | 10.34 – 10.75 | 12 | 12 | — |

### Better-Auth: lint deps (Knip)

Seconds · lower is better

_Namespace leads · Blaxel is ~1.3× higher (lower is better)._

| Rank | Provider | Better-Auth: lint deps (Knip) (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 8.043 | 7.926 – 8.093 | 12 | 12 | — |
| 2 | Blaxel | 10.2 | 9.785 – 10.4 | 12 | 12 | — |
| 2 | Daytona (VM) | 10.49 | 10.13 – 10.65 | 12 | 12 | tied |
| 4 | Microsandbox Cloud | 12.65 | 12.42 – 12.78 | 12 | 12 | — |
| 4 | Novita | 13.39 | 11.95 – 15.67 | 12 | 12 | tied |
| 4 | Modal (VM) | 13.4 | 13.27 – 13.67 | 12 | 12 | tied |
| 7 | E2B | 18.18 | 17.78 – 18.36 | 12 | 12 | — |
| 8 | Modal (gVisor) | 28.78 | 27.92 – 29.19 | 12 | 12 | — |

### Better-Auth: lint format

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.3× higher (lower is better)._

| Rank | Provider | Better-Auth: lint format (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 2.206 | 2.159 – 2.259 | 12 | 12 | — |
| 2 | Daytona (VM) | 2.865 | 2.757 – 3.004 | 12 | 12 | — |
| 2 | Blaxel | 2.997 | 2.961 – 3.12 | 12 | 12 | tied |
| 4 | Microsandbox Cloud | 3.45 | 3.384 – 3.575 | 12 | 12 | — |
| 4 | Novita | 3.581 | 3.132 – 4.221 | 12 | 12 | tied |
| 4 | Modal (VM) | 3.763 | 3.673 – 3.835 | 12 | 12 | tied |
| 7 | E2B | 5.128 | 5.047 – 5.238 | 12 | 12 | — |
| 8 | Modal (gVisor) | 7.208 | 7.004 – 7.435 | 12 | 12 | — |

### Better-Auth: lint packages

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.2× higher (lower is better)._

| Rank | Provider | Better-Auth: lint packages (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 2.04 | 2.008 – 2.063 | 12 | 12 | — |
| 2 | Daytona (VM) | 2.424 | 2.383 – 2.457 | 12 | 12 | — |
| 3 | Blaxel | 2.51 | 2.438 – 2.575 | 12 | 12 | — |
| 4 | Modal (VM) | 3.205 | 3.161 – 3.252 | 12 | 12 | — |
| 4 | Novita | 3.215 | 2.673 – 3.476 | 12 | 12 | tied |
| 4 | Microsandbox Cloud | 3.28 | 3.174 – 3.408 | 12 | 12 | tied |
| 7 | E2B | 4.089 | 4.026 – 4.19 | 12 | 12 | — |
| 8 | Modal (gVisor) | 10.74 | 10.45 – 11 | 12 | 12 | — |

### Better-Auth: lint spell

Seconds · lower is better

_Namespace leads · Blaxel is ~1.3× higher (lower is better)._

| Rank | Provider | Better-Auth: lint spell (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 5.332 | 5.302 – 5.356 | 12 | 12 | — |
| 2 | Blaxel | 7.099 | 6.859 – 7.412 | 12 | 12 | — |
| 2 | Daytona (VM) | 7.181 | 6.772 – 7.612 | 12 | 12 | tied |
| 4 | Modal (VM) | 9.072 | 8.741 – 9.348 | 12 | 12 | — |
| 4 | Novita | 9.274 | 7.744 – 10.21 | 12 | 12 | tied |
| 4 | Microsandbox Cloud | 9.69 | 9.636 – 9.976 | 12 | 12 | tied |
| 7 | E2B | 12.49 | 12.34 – 12.74 | 12 | 12 | — |
| 8 | Modal (gVisor) | 15.79 | 15.48 – 16.19 | 12 | 12 | — |

### Better-Auth: lint types

Seconds · lower is better

_Namespace, Daytona (VM) and Blaxel share the top on this metric (lower is better)._

| Rank | Provider | Better-Auth: lint types (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 24.42 | 23.93 – 24.9 | 12 | 12 | — |
| 1 | Daytona (VM) | 25.16 | 24.04 – 27.54 | 12 | 12 | tied |
| 1 | Blaxel | 27.38 | 26.57 – 28.14 | 12 | 12 | tied |
| 4 | Modal (VM) | 34.58 | 33.48 – 34.98 | 12 | 12 | — |
| 4 | Novita | 35.64 | 33.65 – 42.11 | 12 | 12 | tied |
| 4 | Microsandbox Cloud | 38.55 | 37.84 – 38.75 | 12 | 12 | tied |
| 7 | E2B | 47.21 | 45.91 – 48 | 12 | 12 | — |
| 8 | Modal (gVisor) | 103.2 | 100 – 105.4 | 12 | 12 | — |

### Better-Auth: typecheck

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.3× higher (lower is better)._

| Rank | Provider | Better-Auth: typecheck (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 30.37 | 29.89 – 30.63 | 12 | 12 | — |
| 2 | Daytona (VM) | 40.46 | 38.89 – 40.92 | 12 | 12 | — |
| 3 | Blaxel | 42.14 | 41.01 – 43.62 | 12 | 12 | — |
| 3 | Novita | 48.08 | 41.84 – 56.83 | 12 | 12 | tied |
| 3 | Modal (VM) | 49.71 | 48.61 – 53.6 | 12 | 12 | tied |
| 6 | Microsandbox Cloud | 56.82 | 56.25 – 58.46 | 12 | 12 | — |
| 7 | E2B | 67.72 | 66.43 – 70.25 | 12 | 12 | — |
| 8 | Modal (gVisor) | 77.75 | 75.13 – 81.94 | 12 | 12 | — |

### Mastra: build:core

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.3× higher (lower is better)._

| Rank | Provider | Mastra: build:core (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 55.52 | 55.21 – 55.88 | 12 | 12 | — |
| 2 | Daytona (VM) | 70.66 | 69.96 – 71.11 | 12 | 12 | — |
| 3 | Blaxel | 73.06 | 71.97 – 73.31 | 12 | 12 | — |
| 4 | Novita | 85.03 | 80.05 – 100.3 | 12 | 12 | — |
| 4 | Modal (VM) | 91.94 | 80.86 – 96.01 | 12 | 12 | tied |
| 4 | Microsandbox Cloud | 93.14 | 90.96 – 94.74 | 12 | 12 | tied |
| 7 | E2B | 120.9 | 118.2 – 122.8 | 12 | 12 | — |
| 8 | Modal (gVisor) | 170.5 | 167.8 – 174.9 | 12 | 12 | — |

### Mastra: git clone

Seconds · lower is better

_Blaxel leads · Modal (VM) is ~1.2× higher (lower is better)._

| Rank | Provider | Mastra: git clone (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 2.138 | 1.559 – 2.269 | 12 | 12 | — |
| 2 | Modal (VM) | 2.593 | 2.512 – 2.644 | 12 | 12 | — |
| 2 | Daytona (VM) | 2.643 | 2.23 – 2.819 | 12 | 12 | tied |
| 4 | Novita | 3.341 | 3.07 – 3.583 | 12 | 12 | — |
| 4 | E2B | 3.479 | 3.213 – 4.08 | 12 | 12 | tied |
| 4 | Namespace | 3.92 | 3.554 – 5.223 | 12 | 12 | tied |
| 4 | Microsandbox Cloud | 5.205 | 3.115 – 19.67 | 12 | 12 | tied |
| 4 | Modal (gVisor) | 5.982 | 5.642 – 6.431 | 12 | 12 | tied |

### Mastra: lint:format

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.3× higher (lower is better)._

| Rank | Provider | Mastra: lint:format (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 66.68 | 66.06 – 67.39 | 12 | 12 | — |
| 2 | Daytona (VM) | 87.97 | 84.36 – 94.22 | 12 | 12 | — |
| 2 | Blaxel | 91.58 | 89.58 – 94.34 | 12 | 12 | tied |
| 4 | Novita | 103.4 | 100.8 – 124.3 | 12 | 12 | — |
| 4 | Microsandbox Cloud | 110.5 | 108.4 – 113.3 | 12 | 12 | tied |
| 4 | Modal (VM) | 116.2 | 103 – 116.9 | 12 | 12 | tied |
| 7 | E2B | 154.4 | 151.1 – 155.8 | 12 | 12 | — |
| 8 | Modal (gVisor) | 197.4 | 189.6 – 206.9 | 12 | 12 | — |

### OpenClaw: cold install

Seconds · lower is better

_Blaxel leads · Daytona (VM) is ~1.1× higher (lower is better)._

| Rank | Provider | OpenClaw: cold install (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 11.06 | 10.68 – 11.86 | 12 | 12 | — |
| 2 | Daytona (VM) | 12.69 | 12.56 – 13.24 | 10 | 10 | — |
| 2 | Namespace | 16.9 | 10.31 – 17.37 | 12 | 12 | tied |
| 4 | Novita | 17.82 | 15.87 – 19.2 | 12 | 12 | — |
| 4 | Modal (VM) | 18.03 | 17.73 – 19.47 | 12 | 12 | tied |
| 4 | E2B | 19.59 | 19.35 – 20.63 | 12 | 12 | tied |
| 7 | Modal (gVisor) | 28.36 | 27.48 – 29.3 | 12 | 12 | — |
| 8 | Microsandbox Cloud | 36.69 | 28.89 – 41.87 | 12 | 12 | — |

### OpenClaw: git clone

Seconds · lower is better

_Modal (VM) and Daytona (VM) share the top on this metric (lower is better)._

| Rank | Provider | OpenClaw: git clone (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Modal (VM) | 3.095 | 3.045 – 6.528 | 12 | 12 | — |
| 1 | Daytona (VM) | 3.149 | 3.013 – 3.223 | 10 | 10 | tied |
| 3 | Novita | 4.38 | 4.144 – 4.562 | 12 | 12 | — |
| 3 | Microsandbox Cloud | 4.381 | 4.274 – 17.47 | 12 | 12 | tied |
| 3 | E2B | 4.426 | 4.375 – 5.822 | 12 | 12 | tied |
| 3 | Namespace | 5.966 | 2.645 – 6.024 | 12 | 12 | tied |
| 7 | Blaxel | 7.947 | 4.823 – 8.264 | 12 | 12 | — |
| 8 | Modal (gVisor) | 9.224 | 8.983 – 9.73 | 12 | 12 | — |

### OpenClaw: lint (extension channels)

Seconds · lower is better

_Namespace leads · Blaxel is ~1.2× higher (lower is better)._

| Rank | Provider | OpenClaw: lint (extension channels) (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 52.44 | 48.57 – 54.91 | 12 | 12 | — |
| 2 | Blaxel | 60.64 | 58.99 – 62.21 | 12 | 12 | — |
| 2 | Daytona (VM) | 62.25 | 60.52 – 71.89 | 10 | 10 | tied |
| 4 | Modal (VM) | 75.66 | 73.24 – 76.47 | 12 | 12 | — |
| 4 | Novita | 80.77 | 73.39 – 85.65 | 12 | 12 | tied |
| 6 | Microsandbox Cloud | 86.5 | 82.93 – 89.63 | 12 | 12 | — |
| 7 | E2B | 107.3 | 103.1 – 110.5 | 12 | 12 | — |
| 8 | Modal (gVisor) | 143.9 | 133.8 – 158.9 | 12 | 12 | — |

### OpenClaw: typecheck (test tree)

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.2× higher (lower is better)._

| Rank | Provider | OpenClaw: typecheck (test tree) (Seconds) | 95% bootstrap interval | Sandboxes | Trials |
| ---: | --- | ---: | ---: | ---: | ---: |
| 1 | Namespace | 80.78 | 79.24 – 82.82 | 12 | 12 |
| 2 | Daytona (VM) | 100.2 | 94.96 – 103.7 | 10 | 10 |
| 3 | Modal (VM) | 119 | 117.5 – 126.7 | 12 | 12 |
| 4 | Microsandbox Cloud | 128.8 | 125.3 – 133.4 | 12 | 12 |
| 5 | Novita | 144.5 | 135.3 – 153.8 | 12 | 12 |
| 6 | E2B | 183.2 | 176.6 – 187.4 | 12 | 12 |
| 7 | Modal (gVisor) | 329.1 | 288.8 – 396 | 12 | 12 |

### OpenClaw: typecheck (tsgo)

Seconds · lower is better

_Namespace leads · Blaxel is ~1.3× higher (lower is better)._

| Rank | Provider | OpenClaw: typecheck (tsgo) (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 13.79 | 13.1 – 14.33 | 12 | 12 | — |
| 2 | Blaxel | 17.26 | 16.8 – 17.72 | 12 | 12 | — |
| 2 | Daytona (VM) | 18.08 | 16.81 – 18.55 | 10 | 10 | tied |
| 4 | Modal (VM) | 21.56 | 21.03 – 22.53 | 12 | 12 | — |
| 5 | Microsandbox Cloud | 24.01 | 22.54 – 26.33 | 12 | 12 | — |
| 5 | Novita | 27.52 | 25.55 – 28.87 | 12 | 12 | tied |
| 7 | E2B | 35.44 | 34.49 – 36.38 | 12 | 12 | — |
| 8 | Modal (gVisor) | 59.42 | 43.1 – 68.84 | 12 | 12 | — |

</details>

## cpu

<details>
<summary><strong>1 synthetic metric</strong> · headline: Node.js web tooling</summary>

### Node.js web tooling _(headline)_

runs/s · higher is better

_Namespace leads · ~1.4× Blaxel on median (higher is better)._

| Rank | Provider | Node.js web tooling (runs/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 28.69 | 28.52 – 28.76 | 3 | 9 | — |
| 2 | Blaxel | 19.84 | 19.16 – 20.93 | 3 | 39 | too few sandboxes |
| 3 | Daytona (VM) | 18.95 | 18.87 – 21.06 | 3 | 21 | too few sandboxes |
| 4 | Novita | 18.53 | 14.69 – 19.35 | 3 | 33 | too few sandboxes |
| 5 | Microsandbox Cloud | 17.48 | 17.47 – 17.78 | 3 | 42 | too few sandboxes |
| 6 | Modal (VM) | 14.11 | 11.55 – 19.42 | 3 | 21 | too few sandboxes |
| 7 | E2B | 12.14 | 11.66 – 12.22 | 3 | 9 | too few sandboxes |
| 8 | Modal (gVisor) | 9.4 | 9.2 – 9.64 | 3 | 33 | too few sandboxes |

</details>

## disk

<details>
<summary><strong>9 synthetic metrics</strong> · headline: fio rand read 4KB, O_DIRECT (IOPS)</summary>

### fio rand read 4KB, O_DIRECT (IOPS) _(headline)_

IOPS · higher is better

_Microsandbox Cloud leads · ~1.1× Modal (VM) on median (higher is better)._

| Rank | Provider | fio rand read 4KB, O_DIRECT (IOPS) (IOPS) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Microsandbox Cloud | 317500 | 258500 – 354000 | 3 | 6 | — |
| 2 | Modal (VM) | 286000 | 247000 – 305500 | 3 | 6 | too few sandboxes |
| 3 | Daytona (VM) | 254500 | 235500 – 255500 | 3 | 6 | too few sandboxes |
| 4 | Namespace | 250000 | 249500 – 252000 | 3 | 6 | too few sandboxes |
| 5 | Blaxel | 233000 | 224000 – 239000 | 3 | 6 | too few sandboxes |
| 6 | Novita | 68950 | 67350 – 77150 | 3 | 6 | too few sandboxes |
| 7 | E2B | 46450 | 45600 – 48200 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 32300 | 32100 – 33500 | 3 | 6 | too few sandboxes |

### fio rand read 4KB, O_DIRECT (MB/s)

MB/s · higher is better

_Microsandbox Cloud leads · ~1.1× Modal (VM) on median (higher is better)._

| Rank | Provider | fio rand read 4KB, O_DIRECT (MB/s) (MB/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Microsandbox Cloud | 1241 | 1010 – 1384 | 3 | 6 | — |
| 2 | Modal (VM) | 1118 | 964.5 – 1193 | 3 | 6 | too few sandboxes |
| 3 | Daytona (VM) | 993 | 920 – 999 | 3 | 6 | too few sandboxes |
| 4 | Namespace | 976.5 | 975 – 985.5 | 3 | 6 | too few sandboxes |
| 5 | Blaxel | 910 | 876 – 933 | 3 | 6 | too few sandboxes |
| 6 | Novita | 269.5 | 263.5 – 301.5 | 3 | 6 | too few sandboxes |
| 7 | E2B | 181.5 | 178 – 188 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 126 | 125.5 – 131 | 3 | 6 | too few sandboxes |

### fio rand write 4KB, O_DIRECT (IOPS)

IOPS · higher is better

_Microsandbox Cloud leads · ~1.1× Modal (VM) on median (higher is better)._

| Rank | Provider | fio rand write 4KB, O_DIRECT (IOPS) (IOPS) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Microsandbox Cloud | 304000 | 226500 – 361000 | 3 | 6 | — |
| 2 | Modal (VM) | 281000 | 279000 – 289000 | 3 | 6 | too few sandboxes |
| 3 | Namespace | 240500 | 236500 – 250000 | 3 | 6 | too few sandboxes |
| 4 | Blaxel | 220500 | 204500 – 285500 | 3 | 6 | too few sandboxes |
| 5 | Daytona (VM) | 219500 | 209500 – 226500 | 3 | 6 | too few sandboxes |
| 6 | Novita | 70100 | 69600 – 77850 | 3 | 6 | too few sandboxes |
| 7 | E2B | 48150 | 47100 – 48750 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 27000 | 26200 – 27050 | 3 | 6 | too few sandboxes |

### fio rand write 4KB, O_DIRECT (MB/s)

MB/s · higher is better

_Microsandbox Cloud leads · ~1.1× Modal (VM) on median (higher is better)._

| Rank | Provider | fio rand write 4KB, O_DIRECT (MB/s) (MB/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Microsandbox Cloud | 1189 | 884 – 1411 | 3 | 6 | — |
| 2 | Modal (VM) | 1098 | 1090 – 1129 | 3 | 6 | too few sandboxes |
| 3 | Namespace | 940 | 923.5 – 976.5 | 3 | 6 | too few sandboxes |
| 4 | Blaxel | 861 | 799.5 – 1116 | 3 | 6 | too few sandboxes |
| 5 | Daytona (VM) | 857.5 | 818.5 – 885 | 3 | 6 | too few sandboxes |
| 6 | Novita | 274 | 272 – 304.5 | 3 | 6 | too few sandboxes |
| 7 | E2B | 188 | 183.5 – 190.5 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 105.5 | 102.5 – 105.5 | 3 | 6 | too few sandboxes |

### fio seq read 1MB, O_DIRECT (IOPS)

IOPS · higher is better

_Modal (gVisor) leads · ~1.9× Novita on median (higher is better)._

| Rank | Provider | fio seq read 1MB, O_DIRECT (IOPS) (IOPS) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Modal (gVisor) | 21600 | 19250 – 22750 | 3 | 6 | — |
| 2 | Novita | 11650 | 11500 – 13650 | 3 | 6 | too few sandboxes |
| 3 | Blaxel | 10300 | 7994 – 10850 | 3 | 6 | too few sandboxes |
| 4 | Daytona (VM) | 9329 | 7735 – 12950 | 3 | 6 | too few sandboxes |
| 5 | Microsandbox Cloud | 6652 | 6455 – 8570 | 3 | 6 | too few sandboxes |
| 6 | Namespace | 3983 | 3947 – 4043 | 3 | 6 | too few sandboxes |
| 7 | Modal (VM) | 1724 | 1573 – 1994 | 3 | 6 | too few sandboxes |
| 8 | E2B | 599.5 | 599 – 599.5 | 3 | 6 | too few sandboxes |

### fio seq read 1MB, O_DIRECT (MB/s)

MB/s · higher is better

_Blaxel leads on median (higher is better); see notes for how ranks are decided._

| Rank | Provider | fio seq read 1MB, O_DIRECT (MB/s) (MB/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 8795 | 7996 – 9594 | 2 | 3 | — |
| 2 | Daytona (VM) | 8534 | 7737 – 9331 | 2 | 4 | too few sandboxes |
| 3 | Microsandbox Cloud | 6653 | 6456 – 8571 | 3 | 6 | too few sandboxes |
| 4 | Namespace | 3985 | 3948 – 4045 | 3 | 6 | too few sandboxes |
| 5 | Modal (VM) | 1726 | 1575 – 1996 | 3 | 6 | too few sandboxes |
| 6 | E2B | 601 | 601 – 601 | 3 | 6 | too few sandboxes |

### fio seq write 1MB, O_DIRECT (IOPS)

IOPS · higher is better

_Microsandbox Cloud leads · ~1.1× Novita on median (higher is better)._

| Rank | Provider | fio seq write 1MB, O_DIRECT (IOPS) (IOPS) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Microsandbox Cloud | 7169 | 6438 – 7261 | 3 | 6 | — |
| 2 | Novita | 6459 | 5696 – 6496 | 3 | 6 | too few sandboxes |
| 3 | Blaxel | 5786 | 4934 – 6151 | 3 | 6 | too few sandboxes |
| 4 | Daytona (VM) | 4709 | 3618 – 4837 | 3 | 6 | too few sandboxes |
| 5 | Modal (gVisor) | 3660 | 2961 – 3956 | 3 | 6 | too few sandboxes |
| 6 | Modal (VM) | 2537 | 2396 – 2700 | 3 | 6 | too few sandboxes |
| 7 | Namespace | 2490 | 2455 – 2685 | 3 | 6 | too few sandboxes |
| 8 | E2B | 599.5 | 598.5 – 599.5 | 3 | 6 | too few sandboxes |

### fio seq write 1MB, O_DIRECT (MB/s)

MB/s · higher is better

_Microsandbox Cloud leads · ~1.1× Novita on median (higher is better)._

| Rank | Provider | fio seq write 1MB, O_DIRECT (MB/s) (MB/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Microsandbox Cloud | 7171 | 6440 – 7263 | 3 | 6 | — |
| 2 | Novita | 6460 | 5698 – 6497 | 3 | 6 | too few sandboxes |
| 3 | Blaxel | 5787 | 4936 – 6153 | 3 | 6 | too few sandboxes |
| 4 | Daytona (VM) | 4710 | 3620 – 4839 | 3 | 6 | too few sandboxes |
| 5 | Modal (gVisor) | 3661 | 2963 – 3958 | 3 | 6 | too few sandboxes |
| 6 | Modal (VM) | 2539 | 2397 – 2702 | 3 | 6 | too few sandboxes |
| 7 | Namespace | 2491 | 2456 – 2687 | 3 | 6 | too few sandboxes |
| 8 | E2B | 601 | 600.5 – 601 | 3 | 6 | too few sandboxes |

### Hardlink throughput

bogo ops/s · higher is better

_Daytona (VM) leads · ~1.4× Blaxel on median (higher is better)._

| Rank | Provider | Hardlink throughput (bogo ops/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Daytona (VM) | 26.26 | 22.82 – 26.41 | 3 | 6 | — |
| 2 | Blaxel | 19.14 | 18.89 – 19.66 | 3 | 6 | too few sandboxes |
| 3 | Modal (VM) | 15.64 | 15.44 – 15.67 | 3 | 6 | too few sandboxes |
| 4 | Novita | 12.12 | 11.7 – 12.17 | 3 | 6 | too few sandboxes |
| 5 | Microsandbox Cloud | 9.525 | 8.89 – 9.825 | 3 | 6 | too few sandboxes |
| 6 | Namespace | 5.22 | 5.16 – 5.23 | 3 | 6 | too few sandboxes |
| 7 | Modal (gVisor) | 3.15 | 2.905 – 3.265 | 3 | 6 | too few sandboxes |
| 8 | E2B | 1.415 | 1.4 – 1.43 | 3 | 6 | too few sandboxes |

</details>

## memory

<details>
<summary><strong>4 synthetic metrics</strong> · headline: STREAM Triad</summary>

### STREAM Triad _(headline)_

MB/s · higher is better

_Blaxel leads · ~1.2× Daytona (VM) on median (higher is better)._

| Rank | Provider | STREAM Triad (MB/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 102600 | 101800 – 104000 | 3 | 15 | — |
| 2 | Daytona (VM) | 83120 | 74300 – 96300 | 3 | 15 | too few sandboxes |
| 3 | Modal (VM) | 78470 | 76080 – 123900 | 3 | 15 | too few sandboxes |
| 4 | Modal (gVisor) | 67970 | 64140 – 70620 | 3 | 15 | too few sandboxes |
| 5 | Microsandbox Cloud | 58750 | 58730 – 59130 | 3 | 15 | too few sandboxes |
| 6 | Novita | 50260 | 41930 – 78340 | 3 | 15 | too few sandboxes |
| 7 | E2B | 48870 | 48290 – 50539 | 3 | 15 | too few sandboxes |
| 8 | Namespace | 33690 | 33689 – 33710 | 3 | 15 | too few sandboxes |

### STREAM Add

MB/s · higher is better

_Blaxel leads · ~1.2× Daytona (VM) on median (higher is better)._

| Rank | Provider | STREAM Add (MB/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 102400 | 102100 – 104400 | 3 | 15 | — |
| 2 | Daytona (VM) | 82361 | 74970 – 93530 | 3 | 15 | too few sandboxes |
| 3 | Modal (VM) | 77710 | 75080 – 121400 | 3 | 15 | too few sandboxes |
| 4 | Modal (gVisor) | 63640 | 63455 – 68510 | 3 | 15 | too few sandboxes |
| 5 | Microsandbox Cloud | 58920 | 58629 – 59370 | 3 | 15 | too few sandboxes |
| 6 | Novita | 50270 | 42050 – 77860 | 3 | 15 | too few sandboxes |
| 7 | E2B | 48890 | 48480 – 50695 | 3 | 15 | too few sandboxes |
| 8 | Namespace | 33650 | 33630 – 33690 | 3 | 15 | too few sandboxes |

### STREAM Copy

MB/s · higher is better

_Blaxel leads · ~1.1× Daytona (VM) on median (higher is better)._

| Rank | Provider | STREAM Copy (MB/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 109000 | 100800 – 119800 | 3 | 70 | — |
| 2 | Daytona (VM) | 97560 | 83900 – 110900 | 3 | 70 | too few sandboxes |
| 3 | Modal (VM) | 94360 | 90720 – 114600 | 3 | 15 | too few sandboxes |
| 4 | Modal (gVisor) | 88430 | 87520 – 88950 | 3 | 45 | too few sandboxes |
| 5 | Microsandbox Cloud | 82590 | 81400 – 82820 | 3 | 21 | too few sandboxes |
| 6 | E2B | 78170 | 76090 – 78840 | 3 | 58 | too few sandboxes |
| 7 | Novita | 51600 | 51220 – 56624 | 3 | 55 | too few sandboxes |
| 8 | Namespace | 44260 | 44220 – 44970 | 3 | 15 | too few sandboxes |

### STREAM Scale

MB/s · higher is better

_Blaxel leads · ~1.3× Modal (VM) on median (higher is better)._

| Rank | Provider | STREAM Scale (MB/s) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 94170 | 93230 – 98200 | 3 | 15 | — |
| 2 | Modal (VM) | 74280 | 71790 – 132700 | 3 | 15 | too few sandboxes |
| 3 | Daytona (VM) | 71990 | 67680 – 81460 | 3 | 15 | too few sandboxes |
| 4 | Modal (gVisor) | 56953 | 56880 – 59190 | 3 | 15 | too few sandboxes |
| 5 | Microsandbox Cloud | 50050 | 49210 – 50670 | 3 | 15 | too few sandboxes |
| 6 | Novita | 48540 | 41880 – 77460 | 3 | 15 | too few sandboxes |
| 7 | E2B | 45610 | 45110 – 45960 | 3 | 15 | too few sandboxes |
| 8 | Namespace | 30590 | 30580 – 30610 | 3 | 15 | too few sandboxes |

</details>

## network

<details>
<summary><strong>5 synthetic metrics</strong> · headline: iperf3 loopback TCP, 1 stream</summary>

### iperf3 loopback TCP, 1 stream _(headline)_

Mbits/sec · higher is better

_Novita leads · ~1.3× Blaxel on median (higher is better)._

| Rank | Provider | iperf3 loopback TCP, 1 stream (Mbits/sec) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Novita | 147200 | 43370 – 155500 | 3 | 6 | — |
| 2 | Blaxel | 115700 | 95840 – 134000 | 3 | 6 | too few sandboxes |
| 3 | Daytona (VM) | 84696 | 75276 – 87650 | 3 | 6 | too few sandboxes |
| 4 | Namespace | 71970 | 71720 – 72348 | 3 | 6 | too few sandboxes |
| 5 | Microsandbox Cloud | 67720 | 58740 – 71594 | 3 | 6 | too few sandboxes |
| 6 | E2B | 52440 | 50601 – 66630 | 3 | 6 | too few sandboxes |
| 7 | Modal (VM) | 19068 | 14640 – 22180 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 14760 | 12688 – 15990 | 3 | 6 | too few sandboxes |

### iperf3 loopback TCP, 10 streams

Mbits/sec · higher is better

_Blaxel leads · ~1.3× Novita on median (higher is better)._

| Rank | Provider | iperf3 loopback TCP, 10 streams (Mbits/sec) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 165600 | 106652 – 191100 | 3 | 6 | — |
| 2 | Novita | 132367 | 55682 – 156217 | 3 | 6 | too few sandboxes |
| 3 | Microsandbox Cloud | 75396 | 63790 – 84086 | 3 | 6 | too few sandboxes |
| 4 | Daytona (VM) | 72621 | 47900 – 88200 | 3 | 6 | too few sandboxes |
| 5 | Namespace | 64460 | 63590 – 69580 | 3 | 6 | too few sandboxes |
| 6 | E2B | 44580 | 43181 – 58630 | 3 | 6 | too few sandboxes |
| 7 | Modal (VM) | 15618 | 15290 – 17406 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 14326 | 13030 – 14810 | 3 | 6 | too few sandboxes |

### iperf3 loopback UDP, 10G objective

Mbits/sec · higher is better

_Blaxel, Daytona (VM), E2B, Microsandbox Cloud, Modal (VM), Namespace and Novita share the top on this metric (higher is better)._

| Rank | Provider | iperf3 loopback UDP, 10G objective (Mbits/sec) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 9999 | 9999 – 9999 | 3 | 6 | — |
| 1 | Daytona (VM) | 9999 | 9999 – 9999 | 3 | 6 | too few sandboxes, equal medians |
| 1 | E2B | 9999 | 9999 – 9999 | 3 | 6 | too few sandboxes, equal medians |
| 1 | Microsandbox Cloud | 9999 | 9999 – 9999 | 3 | 6 | too few sandboxes, equal medians |
| 1 | Modal (VM) | 9999 | 9999 – 10000 | 3 | 6 | too few sandboxes, equal medians |
| 1 | Namespace | 9999 | 9999 – 9999 | 3 | 6 | too few sandboxes, equal medians |
| 1 | Novita | 9999 | 9999 – 9999 | 3 | 6 | too few sandboxes, equal medians |
| 8 | Modal (gVisor) | 182.5 | 181.5 – 190.5 | 3 | 6 | too few sandboxes |

### iperf3 WAN download

Mbits/sec · higher is better

_Modal (gVisor) leads · ~1.5× Microsandbox Cloud on median (higher is better)._

| Rank | Provider | iperf3 WAN download (Mbits/sec) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Modal (gVisor) | 8365 | 5802 – 9560 | 3 | 6 | — |
| 2 | Microsandbox Cloud | 5763 | 734.1 – 5770 | 3 | 6 | too few sandboxes |
| 3 | Daytona (VM) | 4529 | 3842 – 5212 | 3 | 6 | too few sandboxes |
| 4 | Namespace | 3702 | 3475 – 12660 | 3 | 6 | too few sandboxes |
| 5 | Novita | 3471 | 422.8 – 4350 | 3 | 6 | too few sandboxes |
| 6 | E2B | 3211 | 936.5 – 4071 | 3 | 6 | too few sandboxes |
| 7 | Modal (VM) | 1401 | 1282 – 1480 | 3 | 6 | too few sandboxes |
| 8 | Blaxel | 1177 | 1044 – 1346 | 3 | 6 | too few sandboxes |

### iperf3 WAN upload

Mbits/sec · higher is better

_Modal (VM) leads · ~1.7× Novita on median (higher is better)._

| Rank | Provider | iperf3 WAN upload (Mbits/sec) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Modal (VM) | 6262 | 5872 – 9283 | 3 | 6 | — |
| 2 | Novita | 3639 | 1163 – 4581 | 3 | 6 | too few sandboxes |
| 3 | E2B | 3314 | 1076 – 3599 | 3 | 6 | too few sandboxes |
| 4 | Daytona (VM) | 3243 | 2728 – 3677 | 3 | 6 | too few sandboxes |
| 5 | Blaxel | 1521 | 880.2 – 1994 | 3 | 6 | too few sandboxes |
| 6 | Microsandbox Cloud | 1463 | 638.6 – 1850 | 3 | 6 | too few sandboxes |
| 7 | Namespace | 1428 | 1064 – 4218 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 141.1 | 140.9 – 150.7 | 3 | 6 | too few sandboxes |

</details>

## system

<details>
<summary><strong>7 synthetic metrics</strong> · headline: PyBench</summary>

### PyBench _(headline)_

Milliseconds · lower is better

_Namespace leads · Daytona (VM) is ~1.1× higher (lower is better)._

| Rank | Provider | PyBench (Milliseconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 364.5 | 362 – 367.5 | 3 | 6 | — |
| 2 | Daytona (VM) | 410 | 406 – 445 | 3 | 6 | too few sandboxes |
| 3 | Novita | 484 | 483.5 – 675.5 | 3 | 6 | too few sandboxes |
| 4 | Blaxel | 490 | 477 – 498.5 | 3 | 6 | too few sandboxes |
| 5 | Microsandbox Cloud | 508.5 | 505.5 – 511 | 3 | 6 | too few sandboxes |
| 6 | Modal (VM) | 672 | 447 – 824 | 3 | 6 | too few sandboxes |
| 7 | E2B | 802.5 | 731.5 – 807 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 897.5 | 896 – 911 | 3 | 6 | too few sandboxes |

### Git common operations

Seconds · lower is better

_Namespace leads · Daytona (VM) is ~1.2× higher (lower is better)._

| Rank | Provider | Git common operations (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 31.93 | 31.72 – 32.05 | 3 | 6 | — |
| 2 | Daytona (VM) | 37.77 | 36.12 – 42.42 | 3 | 6 | too few sandboxes |
| 3 | Blaxel | 42.03 | 42.02 – 45.63 | 3 | 6 | too few sandboxes |
| 4 | Novita | 44.24 | 44.2 – 50.68 | 3 | 6 | too few sandboxes |
| 5 | Microsandbox Cloud | 51.52 | 51.08 – 52.7 | 3 | 6 | too few sandboxes |
| 6 | Modal (VM) | 59.83 | 38.89 – 64.93 | 3 | 6 | too few sandboxes |
| 7 | E2B | 64.11 | 63.36 – 68.37 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 81.14 | 81.09 – 83.91 | 3 | 6 | too few sandboxes |

### pgbench RO (s100, 50c)

TPS · higher is better

_Blaxel leads · ~1.2× Namespace on median (higher is better)._

| Rank | Provider | pgbench RO (s100, 50c) (TPS) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 288600 | 251800 – 300400 | 3 | 6 | — |
| 2 | Namespace | 243600 | 222400 – 252700 | 3 | 6 | too few sandboxes |
| 3 | Microsandbox Cloud | 214500 | 195100 – 223100 | 3 | 6 | too few sandboxes |
| 4 | Modal (VM) | 200700 | 199000 – 322900 | 3 | 6 | too few sandboxes |
| 5 | Novita | 193300 | 165800 – 205700 | 3 | 6 | too few sandboxes |
| 6 | E2B | 177400 | 177000 – 224900 | 3 | 6 | too few sandboxes |
| 7 | Modal (gVisor) | 12040 | 11110 – 12130 | 3 | 6 | too few sandboxes |

### pgbench RO latency (s100, 50c)

ms · lower is better

_Blaxel leads · Namespace is ~1.2× higher (lower is better)._

| Rank | Provider | pgbench RO latency (s100, 50c) (ms) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Blaxel | 0.1735 | 0.1665 – 0.1985 | 3 | 6 | — |
| 2 | Namespace | 0.2055 | 0.198 – 0.228 | 3 | 6 | too few sandboxes |
| 3 | Microsandbox Cloud | 0.2335 | 0.2245 – 0.259 | 3 | 6 | too few sandboxes |
| 4 | Modal (VM) | 0.249 | 0.155 – 0.2515 | 3 | 6 | too few sandboxes |
| 5 | Novita | 0.2585 | 0.244 – 0.3015 | 3 | 6 | too few sandboxes |
| 6 | E2B | 0.282 | 0.2225 – 0.2825 | 3 | 6 | too few sandboxes |
| 7 | Modal (gVisor) | 4.151 | 4.12 – 4.5 | 3 | 6 | too few sandboxes |

### pgbench RW (s100, 50c)

TPS · higher is better

_Namespace leads · ~1.2× Blaxel on median (higher is better)._

| Rank | Provider | pgbench RW (s100, 50c) (TPS) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 26400 | 17640 – 27670 | 3 | 6 | — |
| 2 | Blaxel | 22120 | 22060 – 23490 | 3 | 6 | too few sandboxes |
| 3 | Microsandbox Cloud | 17550 | 16940 – 17900 | 3 | 6 | too few sandboxes |
| 4 | Novita | 14570 | 13600 – 17470 | 3 | 6 | too few sandboxes |
| 5 | Modal (VM) | 13930 | 13900 – 21290 | 3 | 6 | too few sandboxes |
| 6 | E2B | 11760 | 11280 – 13900 | 3 | 6 | too few sandboxes |
| 7 | Modal (gVisor) | 1995 | 1901 – 2022 | 3 | 6 | too few sandboxes |

### pgbench RW latency (s100, 50c)

ms · lower is better

_Namespace leads · Blaxel is ~1.2× higher (lower is better)._

| Rank | Provider | pgbench RW latency (s100, 50c) (ms) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Namespace | 1.894 | 1.807 – 2.852 | 3 | 6 | — |
| 2 | Blaxel | 2.261 | 2.144 – 2.297 | 3 | 6 | too few sandboxes |
| 3 | Microsandbox Cloud | 2.849 | 2.8 – 2.951 | 3 | 6 | too few sandboxes |
| 4 | Novita | 3.434 | 2.862 – 3.678 | 3 | 6 | too few sandboxes |
| 5 | Modal (VM) | 3.591 | 2.35 – 3.598 | 3 | 6 | too few sandboxes |
| 6 | E2B | 4.279 | 3.598 – 4.438 | 3 | 6 | too few sandboxes |
| 7 | Modal (gVisor) | 25.07 | 24.73 – 26.3 | 3 | 6 | too few sandboxes |

### SQLite Speedtest

Seconds · lower is better

_Daytona (VM) leads · Blaxel is ~1.2× higher (lower is better)._

| Rank | Provider | SQLite Speedtest (Seconds) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Daytona (VM) | 33.41 | 31.07 – 39.36 | 3 | 6 | — |
| 2 | Blaxel | 39.03 | 37.19 – 41.86 | 3 | 6 | too few sandboxes |
| 3 | Novita | 41.12 | 40.61 – 59.15 | 3 | 6 | too few sandboxes |
| 4 | Namespace | 48.56 | 48.01 – 48.66 | 3 | 6 | too few sandboxes |
| 5 | Microsandbox Cloud | 57.15 | 56.54 – 59.94 | 3 | 6 | too few sandboxes |
| 6 | Modal (VM) | 66.81 | 32.92 – 91.24 | 3 | 6 | too few sandboxes |
| 7 | E2B | 67.42 | 67.08 – 68.92 | 3 | 6 | too few sandboxes |
| 8 | Modal (gVisor) | 416.4 | 413.5 – 425.1 | 3 | 6 | too few sandboxes |

</details>

## economics

### Hourly cost _(headline)_

USD/hr · lower is better

_Novita is cheapest · Daytona (VM) is ~1.1× higher (lower is better)._

| Rank | Provider | Hourly cost (USD/hr) | 95% bootstrap interval | Sandboxes | Trials | Note |
| ---: | --- | ---: | ---: | ---: | ---: | --- |
| 1 | Novita | 0.2333 | — | 1 | 1 | — |
| 2 | Daytona (VM) | 0.2502 | — | 1 | 1 | — |
| 3 | E2B | 0.3312 | — | 1 | 1 | — |
| 4 | Modal (gVisor) | 0.7612 | — | 1 | 1 | — |
| 4 | Modal (VM) | 0.7612 | — | 1 | 1 | equal values |

## Coverage gaps

22 uncovered results across 8 providers (Blaxel 3, Daytona (VM) 5, E2B 2, Microsandbox Cloud 2, Modal (gVisor) 3, Modal (VM) 2, Namespace 2, Novita 3). A gap is a missing result — the provider **failing to cover** that workload — never a tie or a zero.

<details>
<summary>Full coverage table</summary>

| Provider | Benchmark | Outcome | Detail |
| --- | --- | --- | --- |
| Blaxel | disk | **failed** | PTS duplicate-value dedup dropped 1 fio twin result (MB/s == IOPS at this block size, so the duplicate-valued &lt;Result&gt; was never written): fio_type_sequential_read_engine_linux_aio_direct_yes_block_size_1mb_job_count_1_disk_target_default_test_directory_mb_per_s (twin survived in disk/pts_fio-seq-read.xml) |
| Blaxel | realworld-mastra | **failed** | PTS ran but every trial failed for 1 of 5 declared metrics: realworld_mastra_task_test_core (realworld-mastra/pts_realworld-mastra.xml) — attempted, no value recorded |
| Blaxel | realworld-openclaw | **failed** | PTS ran but every trial failed for 4 of 8 declared metrics: realworld_openclaw_task_lint_oxlint (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_shrinkwrap_check (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_types (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_unit_fast (realworld-openclaw/pts_realworld-openclaw.xml) — attempted, no value recorded |
| Daytona (VM) | disk | **failed** | PTS duplicate-value dedup dropped 1 fio twin result (MB/s == IOPS at this block size, so the duplicate-valued &lt;Result&gt; was never written): fio_type_sequential_read_engine_linux_aio_direct_yes_block_size_1mb_job_count_1_disk_target_default_test_directory_mb_per_s (twin survived in disk/pts_fio-seq-read.xml) |
| Daytona (VM) | pgbench | **failed** | sandbox never ready: no successful "echo ok" in 30 attempts |
| Daytona (VM) | realworld-mastra | **failed** | PTS ran but every trial failed for 1 of 5 declared metrics: realworld_mastra_task_test_core (realworld-mastra/pts_realworld-mastra.xml) — attempted, no value recorded |
| Daytona (VM) | realworld-openclaw | **failed** | PTS ran but every trial failed for 3 of 8 declared metrics: realworld_openclaw_task_lint_oxlint (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_shrinkwrap_check (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_unit_fast (realworld-openclaw/pts_realworld-openclaw.xml) — attempted, no value recorded |
| Daytona (VM) | realworld-openclaw | **failed** | Failed to create sandbox: Failed to create Daytona sandbox: Sandbox failed to start: internal error |
| E2B | realworld-mastra | **failed** | PTS ran but every trial failed for 1 of 5 declared metrics: realworld_mastra_task_test_core (realworld-mastra/pts_realworld-mastra.xml) — attempted, no value recorded |
| E2B | realworld-openclaw | **failed** | PTS ran but every trial failed for 3 of 8 declared metrics: realworld_openclaw_task_lint_oxlint (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_shrinkwrap_check (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_unit_fast (realworld-openclaw/pts_realworld-openclaw.xml) — attempted, no value recorded |
| Microsandbox Cloud | realworld-mastra | **failed** | PTS ran but every trial failed for 1 of 5 declared metrics: realworld_mastra_task_test_core (realworld-mastra/pts_realworld-mastra.xml) — attempted, no value recorded |
| Microsandbox Cloud | realworld-openclaw | **failed** | PTS ran but every trial failed for 3 of 8 declared metrics: realworld_openclaw_task_lint_oxlint (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_shrinkwrap_check (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_unit_fast (realworld-openclaw/pts_realworld-openclaw.xml) — attempted, no value recorded |
| Modal (gVisor) | disk | **failed** | PTS duplicate-value dedup dropped 1 fio twin result (MB/s == IOPS at this block size, so the duplicate-valued &lt;Result&gt; was never written): fio_type_sequential_read_engine_linux_aio_direct_yes_block_size_1mb_job_count_1_disk_target_default_test_directory_mb_per_s (twin survived in disk/pts_fio-seq-read.xml) |
| Modal (gVisor) | realworld-mastra | **failed** | PTS ran but every trial failed for 1 of 5 declared metrics: realworld_mastra_task_test_core (realworld-mastra/pts_realworld-mastra.xml) — attempted, no value recorded |
| Modal (gVisor) | realworld-openclaw | **failed** | PTS ran but every trial failed for 3 of 8 declared metrics: realworld_openclaw_task_lint_oxlint (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_shrinkwrap_check (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_unit_fast (realworld-openclaw/pts_realworld-openclaw.xml) — attempted, no value recorded |
| Modal (VM) | realworld-mastra | **failed** | PTS ran but every trial failed for 1 of 5 declared metrics: realworld_mastra_task_test_core (realworld-mastra/pts_realworld-mastra.xml) — attempted, no value recorded |
| Modal (VM) | realworld-openclaw | **failed** | PTS ran but every trial failed for 3 of 8 declared metrics: realworld_openclaw_task_lint_oxlint (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_shrinkwrap_check (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_unit_fast (realworld-openclaw/pts_realworld-openclaw.xml) — attempted, no value recorded |
| Namespace | realworld-mastra | **failed** | PTS ran but every trial failed for 1 of 5 declared metrics: realworld_mastra_task_test_core (realworld-mastra/pts_realworld-mastra.xml) — attempted, no value recorded |
| Namespace | realworld-openclaw | **failed** | PTS ran but every trial failed for 3 of 8 declared metrics: realworld_openclaw_task_lint_oxlint (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_shrinkwrap_check (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_unit_fast (realworld-openclaw/pts_realworld-openclaw.xml) — attempted, no value recorded |
| Novita | disk | **failed** | PTS duplicate-value dedup dropped 1 fio twin result (MB/s == IOPS at this block size, so the duplicate-valued &lt;Result&gt; was never written): fio_type_sequential_read_engine_linux_aio_direct_yes_block_size_1mb_job_count_1_disk_target_default_test_directory_mb_per_s (twin survived in disk/pts_fio-seq-read.xml) |
| Novita | realworld-mastra | **failed** | PTS ran but every trial failed for 1 of 5 declared metrics: realworld_mastra_task_test_core (realworld-mastra/pts_realworld-mastra.xml) — attempted, no value recorded |
| Novita | realworld-openclaw | **failed** | PTS ran but every trial failed for 3 of 8 declared metrics: realworld_openclaw_task_lint_oxlint (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_shrinkwrap_check (realworld-openclaw/pts_realworld-openclaw.xml), realworld_openclaw_task_test_unit_fast (realworld-openclaw/pts_realworld-openclaw.xml) — attempted, no value recorded |

**failed** — the benchmark was attempted and broke: it threw, timed out, or died with the sandbox.
Unlike a skip, this is a reliability fact about the provider, not a decision made on its behalf.

</details>

<details>
<summary>How rankings are decided</summary>

The value is the median of the PER-SANDBOX medians — one machine, one vote — not the median of all
trials pooled together. Pooling would weight each machine by how many trials it ran, and the harness
chooses that count adaptively by watching the variance, so the noisiest machine would carry the most
weight in the published number. The median, not the mean, because a single stalled pass drags a mean
far more than it moves a median.

The interval is a cluster bootstrap of that same statistic (10,000 resamples, seeded from the Run id
so the table is reproducible byte-for-byte): whole sandboxes are resampled with replacement, keeping
each machine's trials intact.

**The interval is labelled 95%, and at these sandbox counts it does not achieve 95%.** Coverage is a
property of how many machines were measured, not of the estimator: simulated at ≈77% for 3 sandboxes,
≈92% at 6, and ≈95% at 20. No percentile bootstrap reaches nominal coverage at 3 clusters. Read a
3-sandbox interval as a resampling envelope over three machines, **not** as a calibrated frequentist
confidence interval. Within-sandbox trials may also be dependent on host scheduling.

Rows are separated only when Mann-Whitney U (two-sided, α = 0.05, enumerated exactly
over the permutation null rather than approximated) finds evidence of stochastic ordering — at these
sample sizes the normal approximation can report a p the exact test cannot actually produce. Where
replicate sandboxes exist that test runs on the PER-SANDBOX MEDIANS, so whole machines are the
exchangeable unit; testing pooled trials instead would treat repeated measurements of one machine as
independent evidence about the provider. KS is reported separately for distribution *shape* and does
not drive the ranking.

**A Note cell always says why a rank is shared, and the reasons are not interchangeable.**
`tied` — the test could have separated those providers and did not, so a faster median earned
inside the noise is not a faster provider. This is the only note that claims two providers are
statistically indistinguishable.
`equal medians` / `equal values` — arithmetic, not a finding: the ranking sorts on the value,
and two identical values have no order between them. It says nothing about the distributions.

Each metric is measured on several independent sandboxes (the **Sandboxes** column), and within each
sandbox the benchmark runs several trials (**Trials**). Trials capture within-machine noise —
neighbours, host contention, virtualization; sandboxes capture the machine-to-machine variation a
user actually experiences when they start a new environment. The ranking and its interval both treat
the SANDBOX as the unit, so more trials on the same machine never make a row look better-evidenced.
Under adaptive trial counts a large **Trials** figure is in fact a sign the machines were unstable
(the harness kept re-running), not that the estimate is precise.

At the sandbox counts this suite produces, a non-significant result means *not enough evidence to
separate*, never *the providers are equal*.

`too few sandboxes` is the extreme of that: the deciding test's best attainable p already exceeds α,
so it could not have separated the rows at any effect size, however far apart their values are.
The floor is a property of the design — here 2 v 2 sandboxes floors at p ≈ 0.33; 2 v 3 sandboxes floors at p ≈ 0.20; 3 v 3 sandboxes floors at p ≈ 0.10.
At three sandboxes a side the floor is 2/C(6,3) = 0.1, which is above α, so **no** three-sandbox
comparison in this table can ever be declared separated. That is a fact about the replicate count,
not about the providers.
Such rows are ranked on their observed medians and are **not** claimed to be tied — read the gap
between the values, and treat the p-value as unable to settle them either way. Where such a row
nevertheless shares the rank above it, the note reads `equal medians`: the two values are simply
identical, which is the ranking having nothing to order them by — never a finding that the
providers are alike.

### Pairwise tests (vs. row above)

`p vs. above` is the SANDBOX-LEVEL test that decides the rank wherever replicate sandboxes exist —
Mann-Whitney U on each provider's per-sandbox medians, whole machines as the exchangeable unit.
(Only where a provider ran in a single sandbox does it fall back to Mann-Whitney on pooled trials,
which treats repeated measurements of one machine as independent and is anti-conservative.)
`p (KS)` is Kolmogorov-Smirnov on distribution
*shape* — it does not drive the ranking. A tied Mann-Whitney beside a small KS often means the
same typical speed with different behaviour (e.g. bimodal stalls).
These are unadjusted, exploratory per-comparison p-values; no family-wise or false-discovery-rate
correction is applied across providers or metrics.

| Dimension | Metric | Provider | p vs. above | p (KS) |
| --- | --- | --- | ---: | ---: |
| realworld | Mastra: cold install | Blaxel | — | — |
| realworld | Mastra: cold install | Daytona (VM) | 0.48 (tied) | 0.79 |
| realworld | Mastra: cold install | Novita | <0.001 | <0.001 |
| realworld | Mastra: cold install | Modal (VM) | 0.98 (tied) | 0.79 |
| realworld | Mastra: cold install | Namespace | 0.51 (tied) | 0.43 |
| realworld | Mastra: cold install | Microsandbox Cloud | 0.010 | 0.066 |
| realworld | Mastra: cold install | E2B | 0.028 | 0.0046 |
| realworld | Mastra: cold install | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: build | Namespace | — | — |
| realworld | Better-Auth: build | Daytona (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: build | Blaxel | 0.039 | 0.019 |
| realworld | Better-Auth: build | Modal (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: build | Novita | 0.35 (tied) | 0.79 |
| realworld | Better-Auth: build | Microsandbox Cloud | 0.59 (tied) | 0.066 |
| realworld | Better-Auth: build | E2B | <0.001 | <0.001 |
| realworld | Better-Auth: build | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: cold install | Blaxel | — | — |
| realworld | Better-Auth: cold install | Daytona (VM) | 0.028 | 0.066 |
| realworld | Better-Auth: cold install | Novita | <0.001 | <0.001 |
| realworld | Better-Auth: cold install | Microsandbox Cloud | 0.10 (tied) | 0.019 |
| realworld | Better-Auth: cold install | E2B | 0.045 | 0.0046 |
| realworld | Better-Auth: cold install | Modal (VM) | 0.24 (tied) | 0.19 |
| realworld | Better-Auth: cold install | Namespace | 0.51 (tied) | 0.066 |
| realworld | Better-Auth: cold install | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: git clone | Blaxel | — | — |
| realworld | Better-Auth: git clone | Modal (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: git clone | E2B | 0.0029 | <0.001 |
| realworld | Better-Auth: git clone | Daytona (VM) | 0.29 (tied) | 0.19 |
| realworld | Better-Auth: git clone | Namespace | 0.71 (tied) | 0.066 |
| realworld | Better-Auth: git clone | Novita | 0.0029 | 0.066 |
| realworld | Better-Auth: git clone | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: git clone | Microsandbox Cloud | <0.001 | <0.001 |
| realworld | Better-Auth: lint (Biome) | Namespace | — | — |
| realworld | Better-Auth: lint (Biome) | Daytona (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: lint (Biome) | Blaxel | 0.028 | 0.066 |
| realworld | Better-Auth: lint (Biome) | Modal (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: lint (Biome) | Microsandbox Cloud | 0.51 (tied) | 0.43 |
| realworld | Better-Auth: lint (Biome) | Novita | 0.76 (tied) | 0.19 |
| realworld | Better-Auth: lint (Biome) | E2B | <0.001 | <0.001 |
| realworld | Better-Auth: lint (Biome) | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: lint deps (Knip) | Namespace | — | — |
| realworld | Better-Auth: lint deps (Knip) | Blaxel | <0.001 | <0.001 |
| realworld | Better-Auth: lint deps (Knip) | Daytona (VM) | 0.054 (tied) | 0.066 |
| realworld | Better-Auth: lint deps (Knip) | Microsandbox Cloud | <0.001 | <0.001 |
| realworld | Better-Auth: lint deps (Knip) | Novita | 0.38 (tied) | 0.066 |
| realworld | Better-Auth: lint deps (Knip) | Modal (VM) | 0.84 (tied) | 0.19 |
| realworld | Better-Auth: lint deps (Knip) | E2B | <0.001 | <0.001 |
| realworld | Better-Auth: lint deps (Knip) | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: lint format | Namespace | — | — |
| realworld | Better-Auth: lint format | Daytona (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: lint format | Blaxel | 0.078 (tied) | 0.066 |
| realworld | Better-Auth: lint format | Microsandbox Cloud | <0.001 | <0.001 |
| realworld | Better-Auth: lint format | Novita | 1.0 (tied) | 0.066 |
| realworld | Better-Auth: lint format | Modal (VM) | 0.97 (tied) | 0.19 |
| realworld | Better-Auth: lint format | E2B | <0.001 | <0.001 |
| realworld | Better-Auth: lint format | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: lint packages | Namespace | — | — |
| realworld | Better-Auth: lint packages | Daytona (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: lint packages | Blaxel | 0.039 | 0.066 |
| realworld | Better-Auth: lint packages | Modal (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: lint packages | Novita | 0.84 (tied) | 0.19 |
| realworld | Better-Auth: lint packages | Microsandbox Cloud | 0.59 (tied) | 0.066 |
| realworld | Better-Auth: lint packages | E2B | <0.001 | <0.001 |
| realworld | Better-Auth: lint packages | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: lint spell | Namespace | — | — |
| realworld | Better-Auth: lint spell | Blaxel | <0.001 | <0.001 |
| realworld | Better-Auth: lint spell | Daytona (VM) | 0.93 (tied) | 0.43 |
| realworld | Better-Auth: lint spell | Modal (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: lint spell | Novita | 0.93 (tied) | 0.19 |
| realworld | Better-Auth: lint spell | Microsandbox Cloud | 0.59 (tied) | 0.066 |
| realworld | Better-Auth: lint spell | E2B | <0.001 | <0.001 |
| realworld | Better-Auth: lint spell | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: lint types | Namespace | — | — |
| realworld | Better-Auth: lint types | Daytona (VM) | 0.20 (tied) | 0.19 |
| realworld | Better-Auth: lint types | Blaxel | 0.068 (tied) | 0.019 |
| realworld | Better-Auth: lint types | Modal (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: lint types | Novita | 0.29 (tied) | 0.19 |
| realworld | Better-Auth: lint types | Microsandbox Cloud | 0.20 (tied) | 0.019 |
| realworld | Better-Auth: lint types | E2B | <0.001 | <0.001 |
| realworld | Better-Auth: lint types | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Better-Auth: typecheck | Namespace | — | — |
| realworld | Better-Auth: typecheck | Daytona (VM) | <0.001 | <0.001 |
| realworld | Better-Auth: typecheck | Blaxel | 0.0011 | 0.0046 |
| realworld | Better-Auth: typecheck | Novita | 0.13 (tied) | 0.066 |
| realworld | Better-Auth: typecheck | Modal (VM) | 0.76 (tied) | 0.19 |
| realworld | Better-Auth: typecheck | Microsandbox Cloud | <0.001 | <0.001 |
| realworld | Better-Auth: typecheck | E2B | <0.001 | <0.001 |
| realworld | Better-Auth: typecheck | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Mastra: build:core | Namespace | — | — |
| realworld | Mastra: build:core | Daytona (VM) | <0.001 | <0.001 |
| realworld | Mastra: build:core | Blaxel | 0.014 | 0.019 |
| realworld | Mastra: build:core | Novita | <0.001 | <0.001 |
| realworld | Mastra: build:core | Modal (VM) | 0.80 (tied) | 0.79 |
| realworld | Mastra: build:core | Microsandbox Cloud | 0.63 (tied) | 0.43 |
| realworld | Mastra: build:core | E2B | <0.001 | <0.001 |
| realworld | Mastra: build:core | Modal (gVisor) | <0.001 | <0.001 |
| realworld | Mastra: git clone | Blaxel | — | — |
| realworld | Mastra: git clone | Modal (VM) | <0.001 | <0.001 |
| realworld | Mastra: git clone | Daytona (VM) | 0.90 (tied) | 0.43 |
| realworld | Mastra: git clone | Novita | <0.001 | <0.001 |
| realworld | Mastra: git clone | E2B | 0.14 (tied) | 0.19 |
| realworld | Mastra: git clone | Namespace | 0.14 (tied) | 0.19 |
| realworld | Mastra: git clone | Microsandbox Cloud | 0.76 (tied) | 0.066 |
| realworld | Mastra: git clone | Modal (gVisor) | 1.0 (tied) | 0.066 |
| realworld | Mastra: lint:format | Namespace | — | — |
| realworld | Mastra: lint:format | Daytona (VM) | <0.001 | <0.001 |
| realworld | Mastra: lint:format | Blaxel | 0.24 (tied) | 0.19 |
| realworld | Mastra: lint:format | Novita | <0.001 | <0.001 |
| realworld | Mastra: lint:format | Microsandbox Cloud | 0.41 (tied) | 0.019 |
| realworld | Mastra: lint:format | Modal (VM) | 0.63 (tied) | 0.19 |
| realworld | Mastra: lint:format | E2B | <0.001 | <0.001 |
| realworld | Mastra: lint:format | Modal (gVisor) | <0.001 | <0.001 |
| realworld | OpenClaw: cold install | Blaxel | — | — |
| realworld | OpenClaw: cold install | Daytona (VM) | <0.001 | <0.001 |
| realworld | OpenClaw: cold install | Namespace | 0.54 (tied) | 0.028 |
| realworld | OpenClaw: cold install | Novita | 0.033 | 0.019 |
| realworld | OpenClaw: cold install | Modal (VM) | 0.48 (tied) | 0.43 |
| realworld | OpenClaw: cold install | E2B | 0.068 (tied) | 0.019 |
| realworld | OpenClaw: cold install | Modal (gVisor) | <0.001 | <0.001 |
| realworld | OpenClaw: cold install | Microsandbox Cloud | 0.017 | 0.0046 |
| realworld | OpenClaw: git clone | Modal (VM) | — | — |
| realworld | OpenClaw: git clone | Daytona (VM) | 0.54 (tied) | 0.49 |
| realworld | OpenClaw: git clone | Novita | <0.001 | <0.001 |
| realworld | OpenClaw: git clone | Microsandbox Cloud | 0.48 (tied) | 0.43 |
| realworld | OpenClaw: git clone | E2B | 0.80 (tied) | 0.43 |
| realworld | OpenClaw: git clone | Namespace | 0.67 (tied) | 0.19 |
| realworld | OpenClaw: git clone | Blaxel | 0.045 | 0.0046 |
| realworld | OpenClaw: git clone | Modal (gVisor) | <0.001 | <0.001 |
| realworld | OpenClaw: lint (extension channels) | Namespace | — | — |
| realworld | OpenClaw: lint (extension channels) | Blaxel | <0.001 | <0.001 |
| realworld | OpenClaw: lint (extension channels) | Daytona (VM) | 0.12 (tied) | 0.27 |
| realworld | OpenClaw: lint (extension channels) | Modal (VM) | <0.001 | 0.0017 |
| realworld | OpenClaw: lint (extension channels) | Novita | 0.29 (tied) | 0.066 |
| realworld | OpenClaw: lint (extension channels) | Microsandbox Cloud | 0.039 | 0.066 |
| realworld | OpenClaw: lint (extension channels) | E2B | 0.0018 | <0.001 |
| realworld | OpenClaw: lint (extension channels) | Modal (gVisor) | <0.001 | <0.001 |
| realworld | OpenClaw: typecheck (test tree) | Namespace | — | — |
| realworld | OpenClaw: typecheck (test tree) | Daytona (VM) | <0.001 | <0.001 |
| realworld | OpenClaw: typecheck (test tree) | Modal (VM) | <0.001 | <0.001 |
| realworld | OpenClaw: typecheck (test tree) | Microsandbox Cloud | 0.024 | 0.019 |
| realworld | OpenClaw: typecheck (test tree) | Novita | 0.012 | 0.019 |
| realworld | OpenClaw: typecheck (test tree) | E2B | <0.001 | <0.001 |
| realworld | OpenClaw: typecheck (test tree) | Modal (gVisor) | <0.001 | <0.001 |
| realworld | OpenClaw: typecheck (tsgo) | Namespace | — | — |
| realworld | OpenClaw: typecheck (tsgo) | Blaxel | <0.001 | <0.001 |
| realworld | OpenClaw: typecheck (tsgo) | Daytona (VM) | 0.14 (tied) | 0.19 |
| realworld | OpenClaw: typecheck (tsgo) | Modal (VM) | 0.0015 | <0.001 |
| realworld | OpenClaw: typecheck (tsgo) | Microsandbox Cloud | 0.0068 | 0.0046 |
| realworld | OpenClaw: typecheck (tsgo) | Novita | 0.078 (tied) | 0.019 |
| realworld | OpenClaw: typecheck (tsgo) | E2B | <0.001 | <0.001 |
| realworld | OpenClaw: typecheck (tsgo) | Modal (gVisor) | 0.0068 | <0.001 |
| cpu | Node.js web tooling | Namespace | — | — |
| cpu | Node.js web tooling | Blaxel | 0.10 (too few sandboxes) | <0.001 |
| cpu | Node.js web tooling | Daytona (VM) | 0.70 (too few sandboxes) | 0.27 |
| cpu | Node.js web tooling | Novita | 0.40 (too few sandboxes) | <0.001 |
| cpu | Node.js web tooling | Microsandbox Cloud | 0.70 (too few sandboxes) | <0.001 |
| cpu | Node.js web tooling | Modal (VM) | 0.70 (too few sandboxes) | <0.001 |
| cpu | Node.js web tooling | E2B | 0.70 (too few sandboxes) | <0.001 |
| cpu | Node.js web tooling | Modal (gVisor) | 0.10 (too few sandboxes) | <0.001 |
| disk | fio rand read 4KB, O_DIRECT (IOPS) | Microsandbox Cloud | — | — |
| disk | fio rand read 4KB, O_DIRECT (IOPS) | Modal (VM) | 0.40 (too few sandboxes) | 0.81 |
| disk | fio rand read 4KB, O_DIRECT (IOPS) | Daytona (VM) | 0.40 (too few sandboxes) | 0.077 |
| disk | fio rand read 4KB, O_DIRECT (IOPS) | Namespace | 0.70 (too few sandboxes) | 0.81 |
| disk | fio rand read 4KB, O_DIRECT (IOPS) | Blaxel | 0.10 (too few sandboxes) | 0.077 |
| disk | fio rand read 4KB, O_DIRECT (IOPS) | Novita | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand read 4KB, O_DIRECT (IOPS) | E2B | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand read 4KB, O_DIRECT (IOPS) | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand read 4KB, O_DIRECT (MB/s) | Microsandbox Cloud | — | — |
| disk | fio rand read 4KB, O_DIRECT (MB/s) | Modal (VM) | 0.40 (too few sandboxes) | 0.81 |
| disk | fio rand read 4KB, O_DIRECT (MB/s) | Daytona (VM) | 0.40 (too few sandboxes) | 0.077 |
| disk | fio rand read 4KB, O_DIRECT (MB/s) | Namespace | 0.70 (too few sandboxes) | 0.81 |
| disk | fio rand read 4KB, O_DIRECT (MB/s) | Blaxel | 0.10 (too few sandboxes) | 0.012 |
| disk | fio rand read 4KB, O_DIRECT (MB/s) | Novita | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand read 4KB, O_DIRECT (MB/s) | E2B | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand read 4KB, O_DIRECT (MB/s) | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand write 4KB, O_DIRECT (IOPS) | Microsandbox Cloud | — | — |
| disk | fio rand write 4KB, O_DIRECT (IOPS) | Modal (VM) | 0.70 (too few sandboxes) | 0.32 |
| disk | fio rand write 4KB, O_DIRECT (IOPS) | Namespace | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand write 4KB, O_DIRECT (IOPS) | Blaxel | 0.70 (too few sandboxes) | 0.077 |
| disk | fio rand write 4KB, O_DIRECT (IOPS) | Daytona (VM) | 1.0 (too few sandboxes) | 0.81 |
| disk | fio rand write 4KB, O_DIRECT (IOPS) | Novita | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand write 4KB, O_DIRECT (IOPS) | E2B | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand write 4KB, O_DIRECT (IOPS) | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand write 4KB, O_DIRECT (MB/s) | Microsandbox Cloud | — | — |
| disk | fio rand write 4KB, O_DIRECT (MB/s) | Modal (VM) | 0.70 (too few sandboxes) | 0.32 |
| disk | fio rand write 4KB, O_DIRECT (MB/s) | Namespace | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand write 4KB, O_DIRECT (MB/s) | Blaxel | 0.70 (too few sandboxes) | 0.077 |
| disk | fio rand write 4KB, O_DIRECT (MB/s) | Daytona (VM) | 1.0 (too few sandboxes) | 0.81 |
| disk | fio rand write 4KB, O_DIRECT (MB/s) | Novita | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand write 4KB, O_DIRECT (MB/s) | E2B | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio rand write 4KB, O_DIRECT (MB/s) | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq read 1MB, O_DIRECT (IOPS) | Modal (gVisor) | — | — |
| disk | fio seq read 1MB, O_DIRECT (IOPS) | Novita | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq read 1MB, O_DIRECT (IOPS) | Blaxel | 0.10 (too few sandboxes) | 0.012 |
| disk | fio seq read 1MB, O_DIRECT (IOPS) | Daytona (VM) | 1.0 (too few sandboxes) | 0.81 |
| disk | fio seq read 1MB, O_DIRECT (IOPS) | Microsandbox Cloud | 0.20 (too few sandboxes) | 0.077 |
| disk | fio seq read 1MB, O_DIRECT (IOPS) | Namespace | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq read 1MB, O_DIRECT (IOPS) | Modal (VM) | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq read 1MB, O_DIRECT (IOPS) | E2B | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq read 1MB, O_DIRECT (MB/s) | Blaxel | — | — |
| disk | fio seq read 1MB, O_DIRECT (MB/s) | Daytona (VM) | 0.67 (too few sandboxes) | 0.82 |
| disk | fio seq read 1MB, O_DIRECT (MB/s) | Microsandbox Cloud | 0.40 (too few sandboxes) | 0.25 |
| disk | fio seq read 1MB, O_DIRECT (MB/s) | Namespace | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq read 1MB, O_DIRECT (MB/s) | Modal (VM) | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq read 1MB, O_DIRECT (MB/s) | E2B | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq write 1MB, O_DIRECT (IOPS) | Microsandbox Cloud | — | — |
| disk | fio seq write 1MB, O_DIRECT (IOPS) | Novita | 0.40 (too few sandboxes) | 0.077 |
| disk | fio seq write 1MB, O_DIRECT (IOPS) | Blaxel | 0.40 (too few sandboxes) | 0.32 |
| disk | fio seq write 1MB, O_DIRECT (IOPS) | Daytona (VM) | 0.10 (too few sandboxes) | 0.077 |
| disk | fio seq write 1MB, O_DIRECT (IOPS) | Modal (gVisor) | 0.40 (too few sandboxes) | 0.077 |
| disk | fio seq write 1MB, O_DIRECT (IOPS) | Modal (VM) | 0.10 (too few sandboxes) | 0.012 |
| disk | fio seq write 1MB, O_DIRECT (IOPS) | Namespace | 1.0 (too few sandboxes) | 0.32 |
| disk | fio seq write 1MB, O_DIRECT (IOPS) | E2B | 0.10 (too few sandboxes) | 0.0013 |
| disk | fio seq write 1MB, O_DIRECT (MB/s) | Microsandbox Cloud | — | — |
| disk | fio seq write 1MB, O_DIRECT (MB/s) | Novita | 0.40 (too few sandboxes) | 0.077 |
| disk | fio seq write 1MB, O_DIRECT (MB/s) | Blaxel | 0.40 (too few sandboxes) | 0.32 |
| disk | fio seq write 1MB, O_DIRECT (MB/s) | Daytona (VM) | 0.10 (too few sandboxes) | 0.077 |
| disk | fio seq write 1MB, O_DIRECT (MB/s) | Modal (gVisor) | 0.40 (too few sandboxes) | 0.077 |
| disk | fio seq write 1MB, O_DIRECT (MB/s) | Modal (VM) | 0.10 (too few sandboxes) | 0.012 |
| disk | fio seq write 1MB, O_DIRECT (MB/s) | Namespace | 1.0 (too few sandboxes) | 0.32 |
| disk | fio seq write 1MB, O_DIRECT (MB/s) | E2B | 0.10 (too few sandboxes) | 0.0013 |
| disk | Hardlink throughput | Daytona (VM) | — | — |
| disk | Hardlink throughput | Blaxel | 0.10 (too few sandboxes) | 0.0013 |
| disk | Hardlink throughput | Modal (VM) | 0.10 (too few sandboxes) | 0.0013 |
| disk | Hardlink throughput | Novita | 0.10 (too few sandboxes) | 0.0013 |
| disk | Hardlink throughput | Microsandbox Cloud | 0.10 (too few sandboxes) | 0.0013 |
| disk | Hardlink throughput | Namespace | 0.10 (too few sandboxes) | 0.0013 |
| disk | Hardlink throughput | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| disk | Hardlink throughput | E2B | 0.10 (too few sandboxes) | 0.0013 |
| memory | STREAM Triad | Blaxel | — | — |
| memory | STREAM Triad | Daytona (VM) | 0.10 (too few sandboxes) | 0.0011 |
| memory | STREAM Triad | Modal (VM) | 1.0 (too few sandboxes) | 0.31 |
| memory | STREAM Triad | Modal (gVisor) | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Triad | Microsandbox Cloud | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Triad | Novita | 0.70 (too few sandboxes) | 0.0011 |
| memory | STREAM Triad | E2B | 1.0 (too few sandboxes) | 0.14 |
| memory | STREAM Triad | Namespace | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Add | Blaxel | — | — |
| memory | STREAM Add | Daytona (VM) | 0.10 (too few sandboxes) | 0.0011 |
| memory | STREAM Add | Modal (VM) | 1.0 (too few sandboxes) | 0.31 |
| memory | STREAM Add | Modal (gVisor) | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Add | Microsandbox Cloud | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Add | Novita | 0.70 (too few sandboxes) | 0.0011 |
| memory | STREAM Add | E2B | 1.0 (too few sandboxes) | 0.14 |
| memory | STREAM Add | Namespace | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Copy | Blaxel | — | — |
| memory | STREAM Copy | Daytona (VM) | 0.40 (too few sandboxes) | <0.001 |
| memory | STREAM Copy | Modal (VM) | 1.0 (too few sandboxes) | 0.065 |
| memory | STREAM Copy | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0018 |
| memory | STREAM Copy | Microsandbox Cloud | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Copy | E2B | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Copy | Novita | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Copy | Namespace | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Scale | Blaxel | — | — |
| memory | STREAM Scale | Modal (VM) | 0.70 (too few sandboxes) | 0.0011 |
| memory | STREAM Scale | Daytona (VM) | 0.70 (too few sandboxes) | 0.31 |
| memory | STREAM Scale | Modal (gVisor) | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Scale | Microsandbox Cloud | 0.10 (too few sandboxes) | <0.001 |
| memory | STREAM Scale | Novita | 0.70 (too few sandboxes) | 0.017 |
| memory | STREAM Scale | E2B | 0.70 (too few sandboxes) | 0.0047 |
| memory | STREAM Scale | Namespace | 0.10 (too few sandboxes) | <0.001 |
| network | iperf3 loopback TCP, 1 stream | Novita | — | — |
| network | iperf3 loopback TCP, 1 stream | Blaxel | 0.70 (too few sandboxes) | 0.077 |
| network | iperf3 loopback TCP, 1 stream | Daytona (VM) | 0.10 (too few sandboxes) | 0.0013 |
| network | iperf3 loopback TCP, 1 stream | Namespace | 0.10 (too few sandboxes) | 0.012 |
| network | iperf3 loopback TCP, 1 stream | Microsandbox Cloud | 0.10 (too few sandboxes) | 0.077 |
| network | iperf3 loopback TCP, 1 stream | E2B | 0.20 (too few sandboxes) | 0.32 |
| network | iperf3 loopback TCP, 1 stream | Modal (VM) | 0.10 (too few sandboxes) | 0.0013 |
| network | iperf3 loopback TCP, 1 stream | Modal (gVisor) | 0.40 (too few sandboxes) | 0.32 |
| network | iperf3 loopback TCP, 10 streams | Blaxel | — | — |
| network | iperf3 loopback TCP, 10 streams | Novita | 0.40 (too few sandboxes) | 0.32 |
| network | iperf3 loopback TCP, 10 streams | Microsandbox Cloud | 0.70 (too few sandboxes) | 0.077 |
| network | iperf3 loopback TCP, 10 streams | Daytona (VM) | 1.0 (too few sandboxes) | 0.32 |
| network | iperf3 loopback TCP, 10 streams | Namespace | 0.70 (too few sandboxes) | 0.32 |
| network | iperf3 loopback TCP, 10 streams | E2B | 0.10 (too few sandboxes) | 0.0013 |
| network | iperf3 loopback TCP, 10 streams | Modal (VM) | 0.10 (too few sandboxes) | 0.0013 |
| network | iperf3 loopback TCP, 10 streams | Modal (gVisor) | 0.10 (too few sandboxes) | 0.32 |
| network | iperf3 loopback UDP, 10G objective | Blaxel | — | — |
| network | iperf3 loopback UDP, 10G objective | Daytona (VM) | 1.0 (too few sandboxes, equal medians) | 1.0 |
| network | iperf3 loopback UDP, 10G objective | E2B | 1.0 (too few sandboxes, equal medians) | 1.0 |
| network | iperf3 loopback UDP, 10G objective | Microsandbox Cloud | 1.0 (too few sandboxes, equal medians) | 1.0 |
| network | iperf3 loopback UDP, 10G objective | Modal (VM) | 1.0 (too few sandboxes, equal medians) | 1.0 |
| network | iperf3 loopback UDP, 10G objective | Namespace | 1.0 (too few sandboxes, equal medians) | 1.0 |
| network | iperf3 loopback UDP, 10G objective | Novita | 1.0 (too few sandboxes, equal medians) | 1.0 |
| network | iperf3 loopback UDP, 10G objective | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| network | iperf3 WAN download | Modal (gVisor) | — | — |
| network | iperf3 WAN download | Microsandbox Cloud | 0.10 (too few sandboxes) | 0.012 |
| network | iperf3 WAN download | Daytona (VM) | 0.70 (too few sandboxes) | 0.32 |
| network | iperf3 WAN download | Namespace | 0.70 (too few sandboxes) | 0.81 |
| network | iperf3 WAN download | Novita | 0.40 (too few sandboxes) | 0.32 |
| network | iperf3 WAN download | E2B | 1.0 (too few sandboxes) | 0.81 |
| network | iperf3 WAN download | Modal (VM) | 0.70 (too few sandboxes) | 0.077 |
| network | iperf3 WAN download | Blaxel | 0.20 (too few sandboxes) | 0.077 |
| network | iperf3 WAN upload | Modal (VM) | — | — |
| network | iperf3 WAN upload | Novita | 0.10 (too few sandboxes) | 0.0013 |
| network | iperf3 WAN upload | E2B | 0.40 (too few sandboxes) | 0.32 |
| network | iperf3 WAN upload | Daytona (VM) | 1.0 (too few sandboxes) | 0.81 |
| network | iperf3 WAN upload | Blaxel | 0.10 (too few sandboxes) | 0.012 |
| network | iperf3 WAN upload | Microsandbox Cloud | 0.70 (too few sandboxes) | 0.81 |
| network | iperf3 WAN upload | Namespace | 1.0 (too few sandboxes) | 0.81 |
| network | iperf3 WAN upload | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| system | PyBench | Namespace | — | — |
| system | PyBench | Daytona (VM) | 0.10 (too few sandboxes) | 0.0013 |
| system | PyBench | Novita | 0.10 (too few sandboxes) | 0.0013 |
| system | PyBench | Blaxel | 1.0 (too few sandboxes) | 0.81 |
| system | PyBench | Microsandbox Cloud | 0.10 (too few sandboxes) | 0.012 |
| system | PyBench | Modal (VM) | 0.70 (too few sandboxes) | 0.077 |
| system | PyBench | E2B | 0.70 (too few sandboxes) | 0.077 |
| system | PyBench | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| system | Git common operations | Namespace | — | — |
| system | Git common operations | Daytona (VM) | 0.10 (too few sandboxes) | 0.0013 |
| system | Git common operations | Blaxel | 0.40 (too few sandboxes) | 0.077 |
| system | Git common operations | Novita | 0.40 (too few sandboxes) | 0.077 |
| system | Git common operations | Microsandbox Cloud | 0.10 (too few sandboxes) | 0.0013 |
| system | Git common operations | Modal (VM) | 0.70 (too few sandboxes) | 0.077 |
| system | Git common operations | E2B | 0.40 (too few sandboxes) | 0.077 |
| system | Git common operations | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| system | pgbench RO (s100, 50c) | Blaxel | — | — |
| system | pgbench RO (s100, 50c) | Namespace | 0.20 (too few sandboxes) | 0.012 |
| system | pgbench RO (s100, 50c) | Microsandbox Cloud | 0.20 (too few sandboxes) | 0.012 |
| system | pgbench RO (s100, 50c) | Modal (VM) | 1.0 (too few sandboxes) | 0.32 |
| system | pgbench RO (s100, 50c) | Novita | 0.40 (too few sandboxes) | 0.012 |
| system | pgbench RO (s100, 50c) | E2B | 1.0 (too few sandboxes) | 0.81 |
| system | pgbench RO (s100, 50c) | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| system | pgbench RO latency (s100, 50c) | Blaxel | — | — |
| system | pgbench RO latency (s100, 50c) | Namespace | 0.20 (too few sandboxes) | 0.012 |
| system | pgbench RO latency (s100, 50c) | Microsandbox Cloud | 0.20 (too few sandboxes) | 0.012 |
| system | pgbench RO latency (s100, 50c) | Modal (VM) | 1.0 (too few sandboxes) | 0.32 |
| system | pgbench RO latency (s100, 50c) | Novita | 0.40 (too few sandboxes) | 0.012 |
| system | pgbench RO latency (s100, 50c) | E2B | 1.0 (too few sandboxes) | 0.81 |
| system | pgbench RO latency (s100, 50c) | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| system | pgbench RW (s100, 50c) | Namespace | — | — |
| system | pgbench RW (s100, 50c) | Blaxel | 0.70 (too few sandboxes) | 0.077 |
| system | pgbench RW (s100, 50c) | Microsandbox Cloud | 0.10 (too few sandboxes) | 0.0013 |
| system | pgbench RW (s100, 50c) | Novita | 0.20 (too few sandboxes) | 0.077 |
| system | pgbench RW (s100, 50c) | Modal (VM) | 1.0 (too few sandboxes) | 0.81 |
| system | pgbench RW (s100, 50c) | E2B | 0.20 (too few sandboxes) | 0.012 |
| system | pgbench RW (s100, 50c) | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| system | pgbench RW latency (s100, 50c) | Namespace | — | — |
| system | pgbench RW latency (s100, 50c) | Blaxel | 0.70 (too few sandboxes) | 0.077 |
| system | pgbench RW latency (s100, 50c) | Microsandbox Cloud | 0.10 (too few sandboxes) | 0.0013 |
| system | pgbench RW latency (s100, 50c) | Novita | 0.20 (too few sandboxes) | 0.077 |
| system | pgbench RW latency (s100, 50c) | Modal (VM) | 1.0 (too few sandboxes) | 0.81 |
| system | pgbench RW latency (s100, 50c) | E2B | 0.20 (too few sandboxes) | 0.012 |
| system | pgbench RW latency (s100, 50c) | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| system | SQLite Speedtest | Daytona (VM) | — | — |
| system | SQLite Speedtest | Blaxel | 0.40 (too few sandboxes) | 0.077 |
| system | SQLite Speedtest | Novita | 0.40 (too few sandboxes) | 0.077 |
| system | SQLite Speedtest | Namespace | 0.70 (too few sandboxes) | 0.077 |
| system | SQLite Speedtest | Microsandbox Cloud | 0.10 (too few sandboxes) | 0.0013 |
| system | SQLite Speedtest | Modal (VM) | 0.70 (too few sandboxes) | 0.077 |
| system | SQLite Speedtest | E2B | 0.70 (too few sandboxes) | 0.32 |
| system | SQLite Speedtest | Modal (gVisor) | 0.10 (too few sandboxes) | 0.0013 |
| economics | Hourly cost | Novita | — | — |
| economics | Hourly cost | Daytona (VM) | — | — |
| economics | Hourly cost | E2B | — | — |
| economics | Hourly cost | Modal (gVisor) | — | — |
| economics | Hourly cost | Modal (VM) | — (equal values) | — |

</details>

