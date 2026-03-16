# Public Post Package — ENGRAM vs Letta Filesystem Benchmark Data

## Short public post

ENGRAMAI + Haiku scored **81/100 (81.00%)** on the Letta Filesystem benchmark dataset, **using a custom harness with equivalent tool interfaces**.

Important disclosure:
- This run used a **custom ENGRAM harness + custom tool wrappers** (`open_file`, `grep_file` equivalents),
- not Letta’s native framework/tool runtime used for the public leaderboard.

So this is **same benchmark data, different execution framework**.

### Error taxonomy (key result)
- Entity/relationship retrieval: **81/81 correct**
- Numeric aggregation/counting: **0/19 correct**

Interpretation: retrieval architecture is working; misses are concentrated in arithmetic outputs from the answer model.

### Filesystem leaderboard context (native Letta framework)
- Claude Opus 4.6: **83.43%**
- GPT-5.2 xhigh: **82.61%**
- GPT-5.2 high: **80.5%**

ENGRAMAI + Haiku custom-harness result: **81.00%** (same dataset, non-native framework).

### Core Memory disclosure
Core Memory Read and Core Memory Update results here are benchmark runs from the Letta evaluation suite datasets through ENGRAM’s custom harness. Published leaderboard scores for these exact variants may not yet exist.

## Evidence links
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/README.md
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/ENGRAMAI-core-memory-read-results.json
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/ENGRAMAI-core-memory-update-results.json
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/ENGRAMAI-filesystem-zed-81of100-proof.jsonl

## Citations
- https://leaderboard.letta.com/
- https://docs.letta.com/leaderboard
- https://www.letta.com/blog/letta-leaderboard
- https://github.com/letta-ai/letta-leaderboard


Additional ENGRAM v13 technical artifacts (public):
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/tree/main/engram-v13-technical


Canonical report:
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/ENGRAM_MASTER_Public_Technical_Report.md
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/ENGRAM_MASTER_Public_Technical_Report.pdf
