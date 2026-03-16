# Public Post Draft — ENGRAM LETTA Filesystem Result

ENGRAM just hit **81/100 (81.0%)** on the LETTA-style Filesystem benchmark using Haiku.

Important detail: the failure pattern is clean.
- **Entity + relationship retrieval:** 81/81 correct
- **Numeric aggregation/counting outputs:** 0/19 correct

That means retrieval is not the bottleneck. Arithmetic is.

**Interpretation:**
This is an architecture floor, not a ceiling.
ENGRAM demonstrates strong memory retrieval and reasoning over file-linked entities; misses are concentrated in numeric computation behavior from the answer model.

**Context:**
At drafting time, top filesystem comparator is listed at **83.43% (Opus 4.6 Extended)**.
ENGRAM+Haiku at 81% sits close while using a weaker arithmetic model profile.

**What’s next:**
Run the same harness with a stronger arithmetic model and keep retrieval stack constant. If the miss pattern holds, Filesystem should move materially upward.

## Evidence links
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/README.md
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/ENGRAMAI-core-memory-read-results.json
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/ENGRAMAI-core-memory-update-results.json
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/ENGRAMAI-filesystem-zed-81of100-proof.jsonl
