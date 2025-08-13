# HLS Project Ideas  

These are project proposals for accelerating various computational kernels using **High-Level Synthesis (HLS)** on FPGAs. Each project focuses on leveraging **HLS directives** to create efficient **dataflow pipeline designs** and optimize execution.  
---

### [Sparse Matrix × Dense (SpMM) for GNN Mini‑Batch Inference](./SpMM-GNN.md)
**Application:** Graph Neural Networks (GNNs) are widely used for learning on graph-structured data, such as social networks, recommendation systems, and molecular graphs. In GNN inference, each layer updates node features by aggregating information from neighbors, which requires multiplying a large sparse adjacency matrix with dense feature matrices. Efficiently accelerating this operation enables real-time inference on large graphs for tasks like node classification, link prediction, and graph embedding.  

---

### [Truncated SVD via Gram Builder (Recommender Embeddings)](./Truncated-SVD.md)
**Application:** Truncated Singular Value Decomposition (SVD) is a key technique for dimensionality reduction and matrix factorization in recommender systems. By computing the Gram matrix $G = X^T X$ for a tall-skinny user-item matrix $X$, the system can extract latent factors that capture user and item relationships. Accelerating this step enables scalable embedding generation for large-scale recommendation engines.  

---

### [Blocked Cholesky (LLᵀ) for Portfolio Risk Solves](./Blocked-Cholesky.md)
**Application:** Blocked Cholesky decomposition is essential for solving systems involving symmetric positive definite (SPD) covariance matrices, as found in financial portfolio optimization. Efficiently factorizing large covariance matrices allows rapid risk assessment and optimization, supporting real-time decision-making in trading and asset management.  

---

### [Multi‑Pattern String Matching (Aho–Corasick) for DPI Prefilter](./Aho-Corasick-DPI.md)
**Application:** Multi-pattern string matching is critical for Deep Packet Inspection (DPI) in network security, where payloads are scanned for thousands of known signatures. The Aho–Corasick algorithm enables fast, deterministic matching of multiple patterns in streaming data, supporting intrusion detection and malware filtering at high network speeds.  

---

### [1024‑Point Streaming FFT for OFDM/SDR](./Streaming-FFT.md)
**Application:** Fast Fourier Transform (FFT) is a core operation in wireless communications, especially in OFDM-based physical layers and software-defined radio (SDR) systems. Streaming, high-throughput FFTs enable real-time spectrum analysis, modulation/demodulation, and signal processing for applications such as 5G, Wi-Fi, and cognitive radio.  

---

### [Line‑Buffered Bilinear Resizer for Vision Pre‑processing](./Bilinear-Resizer.md)
**Application:** Bilinear image resizing is a common pre-processing step in computer vision pipelines, especially for deep learning models that require fixed-size inputs. Efficient hardware-based resizing with color conversion and normalization supports real-time video analytics, surveillance, and edge AI deployments.  

---

### [Predicate → Prefix‑Sum (Scan) → Scatter for Column Compaction](./PrefixSum-Scatter.md)
**Application:** Column compaction is widely used in analytics and database engines to filter and compress data based on predicates. By fusing predicate evaluation, prefix-sum (scan), and scatter operations, large datasets can be efficiently processed and compacted in hardware, accelerating query execution and data transformation tasks.  