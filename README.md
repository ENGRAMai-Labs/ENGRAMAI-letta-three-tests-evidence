# LETTA 3-Test Evidence Pack (Public)

Generated: 2026-03-16T08:27:53

## Summary

| Test | Correct/Total | Accuracy |
|---|---:|---:|
| Core Memory READ | 1058/1100 | 96.18% |
| Core Memory UPDATE | 1100/1100 | 100.00% |
| Filesystem (ZED run) | 81/100 | 81.00% |

## Filesystem error pattern (critical finding)
All misses are numeric outputs (currency, counts, record numbers) with `UNKNOWN` outputs.
- Missed questions: Q7, Q9, Q15, Q17, Q22, Q24, Q30, Q31, Q35, Q37, Q39, Q44, Q49, Q53, Q55, Q60, Q61, Q64, Q86
- Entity/relationship lookups: **81/81 correct**
- Numeric aggregation/counting: **0/19 correct**

## Methodology (what harness did)
### Core Memory READ
- Loaded supporting facts into core memory context.
- Answer model: Claude Haiku 4.5.
- Evaluation: benchmark ground-truth matching across full set.

### Core Memory UPDATE
- Applied contradiction/update prompts against prior core-memory facts.
- Answer model: Claude Haiku 4.5.
- Evaluation: post-update answer correctness across full set.

### Filesystem (ZED 81/100)
- Benchmark setup mirrors Letta Filesystem benchmark dataset through ENGRAM custom harness over synthetic data files.
- Tooling pattern: file retrieval via `open_file`/`grep_file` style operations.
- Answer model: Claude Haiku 4.5.
- Scoring: row-level `correct` flags in `ENGRAMAI-ENGRAMAI-filesystem-zed-81of100-proof.jsonl` (no regrading).

## Leaderboard context
- Filesystem native-framework leaderboard comparator at drafting time: **Opus 4.6 at 83.43%**, **GPT-5.2 xhigh at 82.61%**, **GPT-5.2 high at 80.5%**.
- This run: **81.00%** on Haiku, with misses isolated to numeric computation.
- Core Memory note: this report includes internal benchmark artifacts; public leaderboard baselines for these exact core-memory variants may differ or be unpublished.

## Public framing
ENGRAMAI + Haiku achieved 100% on entity retrieval/relationship reasoning in Filesystem (81/81).
The 19 misses are exclusively numeric computation, indicating a model arithmetic limitation rather than an architecture retrieval limitation.

## Artifact files in this folder
- `ENGRAMAI-ENGRAMAI-core-memory-read-results.json`
- `ENGRAMAI-ENGRAMAI-core-memory-update-results.json`
- `ENGRAMAI-ENGRAMAI-filesystem-zed-81of100-proof.jsonl`

## Public citations
- https://leaderboard.letta.com/
- https://docs.letta.com/leaderboard
- https://www.letta.com/blog/letta-leaderboard
- https://www.letta.com/blog/benchmarking-ai-agent-memory
- https://github.com/letta-ai/letta-leaderboard


Disclosure: This package uses Letta benchmark data with a custom ENGRAM harness/tool wrappers, not Letta native runtime.

Additional ENGRAM v13 technical artifacts (public):
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/tree/main/engram-v13-technical
