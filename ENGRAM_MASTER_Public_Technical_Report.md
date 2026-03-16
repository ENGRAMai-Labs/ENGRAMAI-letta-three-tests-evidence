# ENGRAM Master Public Technical Report
Generated: 2026-03-16T11:48:51

**All done on a 16GB RAM Mac Mini...in my basement.**

ENGRAM is a memory architecture for LLM agents focused on state-aware memory resolution across long-running contexts.

Internal benchmarks validated architecture. External benchmarks (Letta datasets + MultiHop-RAG public benchmark) validated against industry/public evaluation data.

## Executive Summary Results
| Benchmark | Result |
|---|---:|
| Letta Core Memory READ | 96.18% (1058/1100) |
| Letta Core Memory UPDATE | 100.00% (1100/1100) |
| Letta Filesystem* | 81.00% (81/100) |
| REAL20 | 98.83% (3953/4000) |
| RULER | 90.15% (1803/2000) |
| BABILong | 88.50% (885/1000) |
| MultiHop-RAG public | 62.56% (1599/2556) vs published GPT-4 56.0% |

* custom harness + equivalent tool interfaces; not native Letta runtime submission

## Letta section (external datasets)
Filesystem error taxonomy: 81/81 entity retrieval, 0/19 numeric aggregation/counting.

## Internal benchmark data tables
Baseline note: Baselines are retrieval configurations in the same harness with the same answer model (Haiku).

### REAL20 (4000q)
| Strategy | Accuracy | Correct/Total | Cost |
|---|---:|---:|---:|
| ENGRAM | 98.83% | 3953/4000 | $9.10 |
| modern_rag | 46.95% | 1878/4000 | $4.84 |
| rag | 64.88% | 2595/4000 | $6.83 |
| vector | 65.15% | 2606/4000 | $7.65 |
| naive | 54.60% | 2184/4000 | $10.90 |
| LlamaIndex(best)† | 71.30% | 570/800 | $0.71 |

### RULER (2000q)
| Strategy | Accuracy | Correct/Total | Cost |
|---|---:|---:|---:|
| ENGRAM | 90.15% | 1803/2000 | $2.68 |
| modern_rag | 82.40% | 1648/2000 | $1.98 |
| rag | 76.05% | 1521/2000 | $1.99 |
| vector | 76.45% | 1529/2000 | $2.28 |
| naive | 55.00% | 1100/2000 | $3.15 |
| LlamaIndex(best)† | 49.00% | n/a | $0.33 |

### BABILong (1000q)
| Strategy | Accuracy | Correct/Total |
|---|---:|---:|
| ENGRAM | 88.50% | 885/1000 |
| modern_rag | 47.30% | 473/1000 |
| rag | 48.50% | 485/1000 |
| vector | 49.40% | 494/1000 |
| naive | 42.90% | 429/1000 |
| LlamaIndex(best)† | 48.40% | 484/1000 |

### BABILong task-level (200/task)
| Task | ENGRAM | LlamaIndex(best) | modern_rag | rag | vector | naive |
|---|---:|---:|---:|---:|---:|---:|
| qa1 | 93.0% | 58.0% | 53.5% | 47.5% | 54.5% | 50.5% |
| qa2 | 83.5% | 0.0% | 0.0% | 6.0% | 0.5% | 10.5% |
| qa3 | 80.0% | 0.0% | 2.0% | 5.0% | 5.0% | 36.5% |
| qa4 | 100.0% | 94.0% | 92.0% | 93.0% | 93.5% | 41.0% |
| qa5 | 86.0% | 90.0% | 89.0% | 91.0% | 93.5% | 76.0% |

† LlamaIndex values are from separate best-config sweep runs (context rows), not primary lane harness rows.

## MultiHop-RAG external validation
- ENGRAM v13 + Haiku: 62.56% (1599/2556), ~55 min full run
- Published GPT-4 baseline: 56.0%
- MultiHop chart includes only validated full-run bars.

## Cost note
- No fixed Opus dollar claim in this report; verify leaderboard cost from live snapshot immediately before distribution.

## Charts included
- Letta Filesystem taxonomy
- REAL20 comparison (includes LlamaIndex†)
- RULER comparison (includes LlamaIndex†)
- BABILong task-level
- MultiHop-RAG validated full-run

Artifacts repo: https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence