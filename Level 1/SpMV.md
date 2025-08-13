# Sparse Matrix-Vector Multiplication (SpMV)

## Introduction  
Sparse Matrix-Vector Multiplication (SpMV) is a key operation in scientific computing and machine learning. Unlike dense matrix multiplication, most entries in a sparse matrix are zero, so storing and computing all elements is inefficient. Instead, SpMV algorithms exploit sparsity to compute results efficiently by skipping zero elements.  

For more details, have a look at https://en.wikipedia.org/wiki/Sparse_matrix%E2%80%93vector_multiplication.

## Applications
- **Scientific computing** (finite element analysis, fluid dynamics)  
- **Graph processing** (PageRank, social network analysis)  
- **Machine learning** (recommendation systems, sparse neural networks)  
- **Search engines** (text indexing using term frequency-inverse document frequency, TF-IDF)  

## Why Accelerate SpMV on FPGA?  
- **Memory-efficient computation**: SpMV avoids redundant zero computations, which suits FPGA architectures with limited on-chip memory.  
- **Streaming-processing computation**: Can be processed using a **compressed format** (e.g., CSR - Compressed Sparse Row) to avoid unnecessary memory accesses.  
- **High parallelism potential**: Non-zero elements can be processed **independently**, allowing **massively parallel execution** on FPGA compute resources.  

## An HLS Design Perspective 
- **Dataflow pipelining (`#pragma HLS dataflow`)** can separate stages (e.g., fetching nonzero values, multiplication, reduction), enabling efficient execution.  
- **Loop pipelining (`#pragma HLS pipeline`)** ensures that matrix elements are processed as soon as they arrive, improving throughput.  
- **Memory partitioning (`#pragma HLS array_partition`)** can optimize access to sparse indices, values, and output vectors to prevent bottlenecks.  
- **Custom hardware-friendly formats** (CSR, COO) can be mapped to FPGA memory structures for efficient read/write operations.  

