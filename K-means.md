# K-Means Clustering

## Introduction  
K-Means is a popular clustering algorithm used for partitioning data into K distinct clusters. It iteratively assigns data points to the nearest cluster centroid and updates the centroids based on the mean of assigned points. The process repeats until convergence, meaning cluster assignments no longer change significantly.  

For more details, have a look at https://en.wikipedia.org/wiki/K-means_clustering.

## Applications
- Image segmentation and compression  
- Anomaly detection in cybersecurity and finance  
- Customer segmentation in marketing and recommendation systems  
- Pattern recognition in bioinformatics and medical imaging  

## Why Accelerate K-Means on FPGA?  
- Large datasets require **high-throughput processing**, making FPGAs well-suited for accelerating clustering on streaming data.  
- K-Means involves repeated **distance computations** and **centroid updates**, which are highly parallelizable.  
- FPGA-based acceleration provides **low-latency, energy-efficient computation** compared to traditional CPUs/GPUs.  

## An HLS Design Perspective  
- **Dataflow pragmas** (`#pragma HLS dataflow`) can be used to separate different stages (distance computation, assignment, and centroid update) for efficient streaming execution.  
- The **distance computation** process can be **fully pipelined** using (`#pragma HLS pipeline`), enabling multiple point evaluations per clock cycle.  
- **Loop unrolling** (`#pragma HLS unroll`) allows multiple cluster distance calculations to run in parallel, improving throughput.  
- Efficient **memory partitioning**  (`#pragma HLS array_partition`) enables simultaneous access to multiple centroids, reducing memory bottlenecks.  

