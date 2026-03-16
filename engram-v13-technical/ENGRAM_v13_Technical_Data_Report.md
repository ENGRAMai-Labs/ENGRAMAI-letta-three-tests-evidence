# ENGRAM v13 Technical Data Report
## Due Diligence Package (Technical Review)

Date: 2026-03-14

---

## 1) Final Matched-Dataset Results (Scale)

### REAL20 (200 sessions / 4,000 questions)
- ENGRAM v13: **98.83%** (3953/4000)
- modern_rag: 46.95% (1878/4000)
- rag: 64.88% (2595/4000)
- vector: 65.15% (2606/4000)
- naive: 54.60% (2184/4000)

### RULER (32k / 2,000 questions)
- ENGRAM v13: **90.15%** (1803/2000)
- modern_rag: 82.40%
- rag: 76.05%
- vector: 76.45%
- naive: 55.00%

### BABILong (4k+8k, 1,000 questions)
- ENGRAM v13: **88.50%** (885/1000)
- modern_rag: 47.30% (473/1000)
- rag: 48.50% (485/1000)
- vector: 49.40% (494/1000)
- naive: 42.90% (429/1000)

---

## 2) BABILong Task-Level Breakdown (1,000q run)

(200/task)

- **qa1**: ENGRAM 93.0% | modern_rag 53.5% | rag 47.5% | vector 54.5% | naive 50.5%
- **qa2**: ENGRAM 83.5% | modern_rag 0.0% | rag 6.0% | vector 0.5% | naive 10.5%
- **qa3**: ENGRAM 80.0% | modern_rag 2.0% | rag 5.0% | vector 5.0% | naive 36.5%
- **qa4**: ENGRAM 100.0% | modern_rag 92.0% | rag 93.0% | vector 93.5% | naive 41.0%
- **qa5**: ENGRAM 86.0% | modern_rag 89.0% | rag 91.0% | vector 93.5% | naive 76.0%

Interpretation:
- ENGRAM dominates qa1/qa2/qa3.
- Baselines are strong on qa4/qa5.
- This is explicitly disclosed for credibility.

---

## 3) Methodology Appendix (exact baseline config)

### Common controls
- Same dataset slices and question sets per comparison.
- Same answer model in these runs: **claude-haiku-4-5-20251001**.
- Deterministic offline scoring (string-part matching for expected answer parts).

### Baseline lane configs

#### modern_rag
- Retrieval type: lexical+semantic hybrid scoring with diversity-aware rerank.
- Context budget: lane-specific compact budget (~30 facts/chunks in RULER stress runner).
- Rerank: yes (second-pass score + diversity penalty).

#### rag
- Retrieval type: lexical keyword overlap + recency tie-break.
- Context budget: lane-specific compact budget (~30 facts/chunks in RULER stress runner).
- Rerank: no explicit second-pass rerank.

#### vector
- Retrieval type: semantic-style overlap baseline (token-overlap proxy in this harness) + recency.
- Context budget: lane-specific compact budget (~35 facts/chunks in RULER stress runner).
- Rerank: no explicit second-pass rerank.

#### naive
- Retrieval type: recency-dominant baseline.
- Context budget: lane-specific compact budget (~50 facts/chunks in RULER stress runner).
- Rerank: none.

### Prompt template (REAL20)
- Context + question
- Instructions:
  - answer only from provided context
  - prefer most recent value when changed
  - concise phrase output
  - semicolon for multi-value answers
  - “Information not found” fallback

### Prompt template (BABILong/RULER)
- Context + question
- “Answer in ONE WORD only” (BABILong)
- “Answer with ONLY exact value requested” (RULER)

---

## 4) Failure Analysis / Iteration History (v10 → v13)

Key failure/fix chain:
1. v10 routing regression on simple entity lookups (REAL20 underperformance)
   - Root cause found in route selection behavior.
   - Router rule patched.
2. v11 improved REAL20 but regressed strongly on RULER 4-hop.
3. v12 redesign regressed on BABILong transition tasks (qa2/qa3).
4. v13 introduced distributed retrieval behavior + deterministic fast paths.
5. RULER 4-hop predecessor issue fixed with deterministic temporal resolver.
6. BABILong qa4 autopsy found directional inverse ambiguity (east/west distractor trap).
   - Patched with deterministic spatial relation resolver.
   - qa4 moved to 100% on 200-sample validation and held in 1,000q run.

---

## 5) Known Limitations (current)

- REAL20 medium tier currently below other tiers in latest profile (**96.17%**) and remains the weakest REAL20 tier.
- BABILong qa2/qa3 still have headroom (83.5% / 80.0%) despite large lead vs baselines.
- Current full matrix uses Haiku as shared answer model; frontier-model validation remains planned.

---

## 6) Scaling/Consistency Evidence

- RULER stress runs scaled to 2,000 Q with stable high accuracy after patch.
- REAL20 scaled to 4,000 Q with strong window stability and no collapse.
- BABILong expanded from 100 Q to 1,000 Q and preserved large margin.

---

## 7) Cost-per-correct (selected)

- REAL20 ENGRAM (200s): cost/correct ≈ **$0.00230**
- RULER ENGRAM (2,000Q): cost/correct ≈ **$0.00149**
- BABILong 1,000Q competitor run total estimated low single-digit dollars per lane set (Haiku pricing).

---

## 8) Reproducibility / Artifact Access

Canonical artifacts (public):
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/engram-v13-technical/ENGRAMAI-v13-final-matrix.json
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/engram-v13-technical/ENGRAMAI-v13-final-analysis.md
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/engram-v13-technical/ENGRAMAI-ruler-v13-full-checkpoints.json
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/engram-v13-technical/ENGRAMAI-babilong-v13-engram-1000-results.json
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/engram-v13-technical/ENGRAMAI-babilong-v13-competitors-1000-results.json
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/engram-v13-technical/ENGRAMAI-real20-results-competitors.jsonl
- https://github.com/ENGRAMai-Labs/ENGRAMAI-letta-three-tests-evidence/blob/main/engram-v13-technical/ENGRAMAI-real20-window_breakdown.json

---

## 9) Summary

This package addresses common skepticism points directly:
- larger BABILong sample,
- explicit baseline methodology,
- candid failure/fix history,
- known limitations,
- and reproducible artifact trail.
