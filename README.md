# HLS Project Ideas  

This repository contains project proposals for accelerating various computational kernels using **High-Level Synthesis (HLS)** on FPGAs. Each project focuses on leveraging **HLS directives** to create efficient **dataflow pipeline designs** and optimize execution.  

## Project List  

### 1. [K-Means Clustering](./K-means.md) 
**Description**: An iterative clustering algorithm that assigns data points to clusters based on proximity to centroids.  
**Applications**: Image segmentation, anomaly detection, recommendation systems.  
**Key HLS Concepts**: Dataflow pipelining, loop unrolling, memory partitioning.  

### 2. [Top-K Selection](./Top-K.md)  
**Description**: Finds the K largest (or smallest) elements in a dataset without full sorting.  
**Applications**: Search engine ranking, packet filtering, recommendation systems.  
**Key HLS Concepts**: Streaming-friendly execution, loop unrolling, dataflow pipelining.  

### 3. [Matrix Multiplication (GEMM)](./GeMM.md)  
**Description**: Computes the product of two matrices, a key operation in linear algebra and ML.  
**Applications**: Deep learning, scientific computing, cryptography.  
**Key HLS Concepts**: Loop pipelining, loop unrolling, memory partitioning.    

### 4. [Image Resizing](./Image-resizing.md)
**Description**: Changes the dimensions of an image, either reducing or increasing its size, while maintaining quality.  
**Applications**: Image processing, computer vision, multimedia applications.  
**Key HLS Concepts**: Dataflow pipelining, loop unrolling, memory partitioning.  

### 5. [RGB to Greyscale Conversion](./RGB-to-grey.md)
**Description**: Converts RGB color images to grayscale by combining the color components into a single intensity value.  
**Applications**: Computer vision, image preprocessing, video processing.  
**Key HLS Concepts**: Dataflow pipelining, loop unrolling, memory partitioning.  

### 6. [QR Decomposition](./QR.md)
**Description**: Decomposes a matrix into an orthogonal matrix $Q$ and an upper triangular matrix $R$.  
**Applications**: Solving linear systems, signal processing, machine learning.  
**Key HLS Concepts**: Dataflow pipelining, loop unrolling, memory partitioning.  

### 7. [Singular Value Decomposition (SVD)](./SVD.md)
**Description**: Decomposes a matrix into three components: $A = U \Sigma V^T$, used in data compression and dimensionality reduction.  
**Applications**: PCA, signal processing, machine learning, data compression.  
**Key HLS Concepts**: Dataflow pipelining, loop unrolling, memory partitioning.  

### 8. [Cholesky Decomposition](./Cholesky.md)
**Description**: Factorizes a positive-definite matrix into the product of a lower triangular matrix and its transpose.  
**Applications**: Solving linear systems, optimization, Kalman filtering, machine learning.  
**Key HLS Concepts**: Dataflow pipelining, loop unrolling, memory partitioning.  

### 9. [Item Frequency Counting](./Count.md)
**Description**: Counts the occurrences of each unique item in a dataset.  
**Applications**: Data mining, database queries, big data processing, e-commerce.  
**Key HLS Concepts**: Dataflow pipelining, loop unrolling, memory partitioning. 

### 10. [1D/2D Convolution](./Convolution.md)  
**Description**: Applies a kernel over a signal or image for feature extraction.  
**Applications**: Signal processing, computer vision, deep learning.  
**Key HLS Concepts**: Dataflow pipelining, loop unrolling, BRAM optimization.  

### 11. [Prefix Sum (Scan Operation)](./Prefix-sum.md)  
**Description**: Computes cumulative sums of an array in parallel.  
**Applications**: Sorting algorithms, image processing, graph traversal.  
**Key HLS Concepts**: Parallel scan, dataflow pipelining, memory partitioning.  

### 12. [Sparse Matrix-Vector Multiplication (SpMV)](./SpMV.md)  
**Description**: Multiplies a sparse matrix with a dense vector, optimizing for nonzero elements.  
**Applications**: Graph processing, scientific computing, search engines.  
**Key HLS Concepts**: Custom memory layouts, dataflow pipelines, loop pipelining.  

### 13. [String Matching (Aho-Corasick, Knuth-Morris-Pratt)](./String-matching.md)  
**Description**: Searches for patterns efficiently within large text datasets.  
**Applications**: Cybersecurity, bioinformatics, search engines.  
**Key HLS Concepts**: FSM acceleration, loop pipelining, memory partitioning.  

### 14. [Fast Fourier Transform (FFT)](./FFT.md)  
**Description**: Efficiently converts signals between time and frequency domains.  
**Applications**: Audio processing, wireless communication, medical imaging.  
**Key HLS Concepts**: Butterfly operation parallelization, loop pipelining, streaming architectures.

## Getting Started  
Each project contains:  
- **A problem description** explaining the computation and its importance.  
- **Applications** where the algorithm is used in real-world scenarios.  
- **Why FPGA acceleration matters**, highlighting the benefits of hardware-based execution.  
- **Why the algorithm works well with HLS**, discussing how directives optimize performance.  

Explore each project for implementation details and potential optimizations using HLS.

