# String Matching

## Introduction  
String matching algorithms are fundamental in searching for patterns within large text datasets. Algorithms like **Aho-Corasick** (multi-pattern matching), **Knuth-Morris-Pratt (KMP)** (efficient single-pattern search), and **Boyer-Moore** (optimized backward scanning) are widely used for fast and efficient text searching. These methods enable quick identification of keywords, DNA sequences, and network packet signatures.  

For more details, have a look at https://en.wikipedia.org/wiki/String-searching_algorithm.

## Applications
- **Bioinformatics** (DNA/RNA sequence alignment)  
- **Cybersecurity** (intrusion detection, malware scanning)  
- **Search engines** (fast keyword retrieval in large databases)  
- **Data compression** (detecting repeated patterns for encoding)  

## Why Accelerate String Matching on FPGA?  
- **High-throughput requirement**: Many real-time applications (e.g., network packet inspection) require processing gigabits of text per second.  
- **Massive parallelism**: FPGA parallelism allows multiple string patterns to be searched **simultaneously**, improving efficiency over CPU-based implementations.  
- **Memory-efficient execution**: Hardware-friendly **finite state machine (FSM)** representations of algorithms like Aho-Corasick reduce redundant comparisons and improve speed.  

## An HLS Design Perspective 
- **Dataflow pipelining (`#pragma HLS dataflow`)** enables independent processing stages (pattern matching, state transitions, and output generation) to run concurrently.  
- **Loop pipelining (`#pragma HLS pipeline`)** ensures continuous processing of incoming text streams with minimal stalls.  
- **Loop unrolling (`#pragma HLS unroll`)** can be applied to check multiple characters or patterns simultaneously, enhancing throughput.  
- **Memory partitioning (`#pragma HLS array_partition`)** optimizes storage of pattern lookup tables and FSM states, preventing memory access bottlenecks.  

