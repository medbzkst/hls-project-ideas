# Blocked Cholesky (LLᵀ) for Portfolio Risk Solves

## Application
Blocked Cholesky decomposition is essential for solving systems involving symmetric positive definite (SPD) covariance matrices, as found in financial portfolio optimization. Efficiently factorizing large covariance matrices allows rapid risk assessment and optimization, supporting real-time decision-making in trading and asset management.

## Context
Markowitz optimization repeatedly solves $\Sigma x=b$ with SPD covariance $\Sigma$.

## Objective
Accelerate **blocked Cholesky** on 64×64 panels, time‑multiplexing potrf/trsm/gemm updates.

## Scope & Partitioning
- **PS:** Build/update $\Sigma$ from returns; manage tile packing; apply constraints post‑solve.
- **PL:** Panel factorization (potrf), triangular solve (trsm), trailing update (gemm) in a wavefront over tiles.

## Data types
FP32 preferred (stability); consider FP16 in / FP32 out with error checks.

## Constraints
Start at **N ≤ 256**; tile = 64×64; double‑buffer panels; ensure diagonal‑panel exclusivity.

## Inputs/Outputs
- **Input:** SPD matrix $\Sigma$ (generate via $A A^T + \lambda I$)
- **Output:** Lower‑triangular $L$ with $\Sigma = L L^T$

## Baseline
PS `scipy.linalg.cholesky` or custom blocked CPU version.

## Targets
- **Residual:** $\|\Sigma - L L^T\|_F/\|\Sigma\|_F ≤ 1e\!−\!6$
