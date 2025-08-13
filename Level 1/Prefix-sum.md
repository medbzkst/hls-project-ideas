# Prefix Sum (Scan Operation)

## Introduction  
The **prefix sum** (also known as the **scan operation**) is a fundamental building block in parallel computing. Given an input array, the prefix sum computes cumulative sums, where each element at index *i* is the sum of all previous elements up to *i*. This operation is widely used in parallel algorithms for data transformation, sorting, and graph processing.  

For more details, have a look at https://en.wikipedia.org/wiki/Prefix_sum.

## Applications
- **Parallel computing** (used in radix sort, stream compaction, and graph traversal)  
- **Image processing** (histogram equalization, cumulative distribution functions)  
- **Finance** (cumulative returns and moving averages)  
- **Cryptography & compression** (Huffman coding, run-length encoding)  

## Why Accelerate Prefix Sum on FPGA?  
- **High parallelism potential**: Instead of a sequential O(N) approach, **tree-based parallel scan algorithms** can achieve **O(log N)** complexity.  
- **Stream-processing computation**: Works well with hardware pipelines to process data as it arrives.  
- **Efficient memory access**: FPGA designs can leverage on-chip BRAMs for fast intermediate storage, minimizing external memory access.  

## An HLS Design Perspective 
- **Loop pipelining (`#pragma HLS pipeline`)** ensures elements are processed with minimal stalls.  
- **Dataflow pragmas (`#pragma HLS dataflow`)** enable multi-stage processing (e.g., up-sweep and down-sweep phases in parallel scan).  
- **Loop unrolling (`#pragma HLS unroll`)** allows multiple elements to be computed simultaneously, improving throughput.  
- **Memory partitioning (`#pragma HLS array_partition`)** optimizes access patterns, reducing bottlenecks when updating partial sums.  

