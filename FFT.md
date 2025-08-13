# Fast Fourier Transform (FFT)

## Introduction  
The **Fast Fourier Transform (FFT)** is a fundamental algorithm for converting signals between the time and frequency domains. It reduces the computational complexity of the Discrete Fourier Transform (DFT) from **O(N²)** to **O(N log N)**, making it critical for real-time signal processing and spectral analysis. FFT is widely used in applications that require frequency domain analysis, filtering, and feature extraction.  

For more details, have a look at https://en.wikipedia.org/wiki/Fast_Fourier_transform.

## Applications
- **Signal processing** (audio processing, radar, and communications)  
- **Machine learning** (spectral feature extraction for speech and image recognition)  
- **Medical imaging** (MRI and CT scan reconstruction)  
- **Wireless communications** (OFDM modulation in 5G, Wi-Fi, LTE)  

## Why Accelerate FFT on FPGA?  
- **Real-time processing requirements**: FFT is heavily used in high-speed applications where **low-latency, high-throughput** processing is required.  
- **Massively parallelizable structure**: The butterfly operations in FFT can be **highly parallelized**, making it ideal for FPGA acceleration.  
- **Custom memory and I/O optimizations**: FPGA designs can leverage **streaming architectures** to avoid memory bottlenecks and maximize efficiency.  

## An HLS Design Perspective 
- **Loop pipelining (`#pragma HLS pipeline`)** ensures that butterfly computations occur continuously, reducing idle cycles.  
- **Dataflow pipelining (`#pragma HLS dataflow`)** allows independent FFT stages (bit-reversal, butterfly computation, scaling) to execute concurrently.  
- **Loop unrolling (`#pragma HLS unroll`)** helps process multiple FFT stages in parallel, improving throughput.  
- **Memory partitioning (`#pragma HLS array_partition`)** optimizes access to intermediate FFT values, reducing memory latency.  

