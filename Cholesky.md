# Cholesky Decomposition 

## Introduction  
Cholesky decomposition is a matrix factorization method for positive-definite matrices, decomposing a matrix $A$ into the product of a lower triangular matrix $L$ and its transpose $L^T$, i.e., $A = LL^T$. This method is widely used in numerical analysis, particularly in solving systems of linear equations and in optimization algorithms where the matrix is guaranteed to be positive-definite.

For more details, have a look at https://en.wikipedia.org/wiki/Cholesky_decomposition.

## Applications  
- **Solving linear systems** (particularly in optimization and simulation)  
- **Monte Carlo simulations** (used in financial modeling, physical simulations)  
- **Kalman filtering** (used in control systems, robotics, and navigation)  
- **Machine learning** (in Gaussian processes and kernel methods)

## Why Accelerate Cholesky Decomposition on FPGA?  
- **High computational demand**: The decomposition involves numerous square root and matrix manipulation operations that can benefit from parallel processing on an FPGA.
- **Low-latency execution**: Applications requiring real-time processing, such as filtering and simulation, can be significantly accelerated on FPGAs.
- **Memory optimization**: FPGAs can optimize memory access patterns to store intermediate results, reducing overall memory latency.

## An HLS Design Perspective 
- **Dataflow pipelining (`#pragma HLS dataflow`)** allows independent stages of the decomposition (like square root computation, row updates) to be executed concurrently.
- **Loop unrolling (`#pragma HLS unroll`)** enables parallel execution of the decomposition for multiple elements in the matrix.
- **Memory partitioning (`#pragma HLS array_partition`)** ensures efficient access to matrix elements and reduces memory bottlenecks during factorization.

