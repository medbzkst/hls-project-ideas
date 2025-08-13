# Truncated SVD via Gram Builder (Recommender Embeddings)

## Application
Truncated Singular Value Decomposition (SVD) is a key technique for dimensionality reduction and matrix factorization in recommender systems. By computing the Gram matrix $G = X^T X$ for a tall-skinny user-item matrix $X$, the system can extract latent factors that capture user and item relationships. Accelerating this step enables scalable embedding generation for large-scale recommendation engines.

## Context
Top‑k SVD powers matrix factorization for recommendations via accelerating **$G=X^T X$** for tall‑skinny $X$.

## Objective
Build $G\in\mathbb{R}^{K\times K}$ on PL by streaming rows of $X$, then finish eig/SVD on PS.

## Scope & Partitioning
- **PS:** Randomized projection/power iteration; orchestrate passes over $X$; final LAPACK eig/SVD on small $G$.
- **PL:** Outer‑product accumulation to **Gram matrix** with INT8 accumulators; optional block TSQR for stability.

## Data types
INT8 input, INT16 accum.

## Constraints
**K ≤ 64** so $G$ fits in BRAM (≈8 KiB in INT16). Single MAC (Multiply-and-Accumulate) array time‑multiplexed across columns.

## Inputs/Outputs
- **Input:** Synthetic or real rating matrix factor (e.g., 100k×64)
- **Output:** $G=X^T X$; PS computes top‑k singular triplets.

## Baseline
PS‑only NumPy `X.T @ X` + `np.linalg.eigh`.

## Targets
- **Error:** relative Frobenius error of $G$ ≤ 1e‑4; top‑k subspace angle ≤ a few degrees
