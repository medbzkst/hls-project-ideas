# Sparse Matrix × Dense (SpMM) for GNN Mini‑Batch Inference

## Application
Graph Neural Networks (GNNs) are widely used for learning on graph-structured data, such as social networks, recommendation systems, and molecular graphs. In GNN inference, each layer updates node features by aggregating information from neighbors, which requires multiplying a large sparse adjacency matrix with dense feature matrices. Efficiently accelerating this operation enables real-time inference on large graphs for tasks like node classification, link prediction, and graph embedding.

## Context
Each GNN layer computes $H' = A\,H\,W$. With large graphs, the multiplication of the sparse $A$ and the dense $H$ dominates.

## Objective
Accelerate a CSR **sparse × dense** tile multiply on the PL. CPU (PS) orchestrates batching and post‑ops.

## Scope & Partitioning
- **PS (ARM):** Load graph, build CSR (`row_ptr, col_idx, val`), bucket rows by degree, prepare dense feature tiles of width **F=64**.
- **PL (FPGA):** Stream CSR rows + corresponding `H` tiles; compute partial sums with INT8 accumulators; optional fused ReLU.

## Data types
`val`: INT8; `H`: INT8; accumulators INT16.

## Constraints
1–2 PEs time‑multiplexed; keep on‑chip tile store ≤ 64×64×1B ≈ 4 KiB per buffer; double‑buffer streams.

## Inputs/Outputs
- **Input:** CSR for a subgraph (≤100k nonzeros per batch), dense features (N×F)
- **Output:** Updated features (N×F) for that batch

## Baseline
CPU SpMM (Scipy/NumPy) on the PS.

## Targets
- **Correctness:** $\|Y_{fpga}-Y_{cpu}\|_\infty/\|Y_{cpu}\|_\infty ≤ 1e{-3}$.
