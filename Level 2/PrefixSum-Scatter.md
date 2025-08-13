# Predicate → Prefix‑Sum (Scan) → Scatter for Column Compaction

## Application
Column compaction is widely used in analytics and database engines to filter and compress data based on predicates. By fusing predicate evaluation, prefix-sum (scan), and scatter operations, large datasets can be efficiently processed and compacted in hardware, accelerating query execution and data transformation tasks.

## Context
Columnar analytics often apply a predicate, scan flags to get indices, then compact the data.

## Objective
Build a streaming **fused pipeline**: predicate (e.g., `x > θ`) → exclusive scan of 0/1 flags → scatter selected values to a compacted output buffer.

## Scope & Partitioning
- **PS:** Generate input columns; choose predicate; verify compaction vs CPU reference; orchestrate two‑pass prefix add if needed.
- **PL:** Tile‑local scan (e.g., 4096 elements) with II=1; write tile sums; second pass adds block prefixes; coalesced scatter writes.

## Data types
32‑ or 64‑bit lanes for values; 1‑bit flags packed into bytes.

## Constraints
Memory‑bound—maximize burst length and alignment; 2–4 elements/clk if BRAM allows.

## Inputs/Outputs
- **Input:** Array `X` (≥10^6 elements), threshold `θ`
- **Output:** Compacted array `Y` and count `M`

## Baseline
PS NumPy mask + `np.nonzero`/`compress`.

## Targets
- **Correctness:** exact compacted output order and count.
