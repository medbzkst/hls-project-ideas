# Multi‑Pattern String Matching (Aho–Corasick) for DPI Prefilter

## Application
Multi-pattern string matching is critical for Deep Packet Inspection (DPI) in network security, where payloads are scanned for thousands of known signatures. The Aho–Corasick algorithm enables fast, deterministic matching of multiple patterns in streaming data, supporting intrusion detection and malware filtering at high network speeds.

## Context
Network IDS inspects payloads against thousands of fixed signatures.

## Objective
Implement a streaming **Aho–Corasick** engine with compact state tables in BRAM; PS handles flow and rules.

## Scope & Partitioning
- **PS:** Compile pattern set (1–2k patterns) → DFA tables; feed packet bytes; collect match events; verify.
- **PL:** Parser → AC next‑state lookup (bit‑split/compressed) → match FIFO → PS.

## Data types
8‑bit symbols; pack 8–16 B/clk depending on LUT/BRAM budget.

## Constraints
Limit alphabet (e.g., lowercase ASCII) or bit‑split to reduce table size; dual‑bank BRAM for hot updates.

## Inputs/Outputs
- **Input:** Byte stream + pattern set
- **Output:** `(pattern_id, position)` events

## Baseline
PS‑only AC (e.g., Python/C) over the same payloads.

## Targets
- **Correctness:** exact match indices equal to CPU baseline
