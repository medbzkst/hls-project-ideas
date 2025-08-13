# QR Decomposition for FPGA Acceleration

## Introduction  
QR decomposition is a matrix factorization technique that decomposes a matrix $A$ into a product of an orthogonal matrix $Q$ and an upper triangular matrix $R$. It is commonly used in numerical linear algebra for solving linear systems, least squares problems, and eigenvalue problems. QR decomposition is a key step in many algorithms in machine learning, signal processing, and computational physics.

Fore more details, have a look at https://en.wikipedia.org/wiki/QR_decomposition.

## Applications  
- **Solving linear systems** ($Ax = b$, least squares problems)  
- **Eigenvalue problems** (used in PCA for dimensionality reduction)  
- **Signal processing** (filtering, compression)  
- **Machine learning** (model training, data transformation)

## Why Accelerate QR Decomposition on FPGA?  
- **High computational intensity**: The process of iteratively performing matrix transformations in QR decomposition is computationally expensive, and an FPGA's parallel nature can speed up these operations.
- **Memory optimization**: FPGAs allow for custom memory layouts and optimized data access patterns, reducing memory latency and improving throughput.
- **Parallelism**: Multiple matrix operations, like the Gram-Schmidt process or Householder transformations, can be efficiently parallelized on FPGA architectures.

## An HLS Design Perspective 
- **Dataflow pipelining (`#pragma HLS dataflow`)** allows for efficient handling of each step in the decomposition, like computing orthogonal vectors and updating the matrix.
- **Loop unrolling (`#pragma HLS unroll`)** can be used to perform multiple iterations of matrix transformations simultaneously, speeding up the computation.
- **Memory partitioning (`#pragma HLS array_partition`)** optimizes access to matrix elements, reducing read/write latencies during factorization.

