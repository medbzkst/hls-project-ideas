# 1D/2D Convolution

## Introduction  
Convolution is a fundamental operation used in signal processing and deep learning. In **1D convolution**, a sliding window is applied over a 1D signal to extract features or smooth the data. In **2D convolution**, commonly used in image processing and neural networks, a kernel slides over an image to detect patterns such as edges or textures.  

For more details, have a look at https://en.wikipedia.org/wiki/Convolution#Discrete_convolution.

## Applications
- **Signal Processing** (audio filtering, equalization, speech recognition)  
- **Computer Vision** (image filtering, edge detection, object recognition)  
- **Deep Learning** (Convolutional Neural Networks for classification, segmentation)  
- **Medical Imaging** (MRI and CT scan analysis)  

## Why Accelerate Convolution on FPGA?  
- **High computational intensity**: Large kernels and high-resolution data require extensive computation, making hardware acceleration essential.  
- **Stream-processing computation**: Convolution naturally fits a **dataflow pipeline** where each element is processed in sequence.  
- **Custom memory access optimization**: Efficient data reuse via **on-chip buffers** (e.g., line buffers for 2D convolution) can significantly reduce memory bandwidth requirements.  

## An HLS Design Perspective  
- **Loop pipelining (`#pragma HLS pipeline`)** ensures continuous data flow, reducing latency.  
- **Loop unrolling (`#pragma HLS unroll`)** enables multiple filter operations to be computed in parallel.  
- **Dataflow pragmas (`#pragma HLS dataflow`)** allow independent stages (data loading, convolution, and storing results) to execute concurrently.  
- **Memory partitioning (`#pragma HLS array_partition`)** can optimize access to input feature maps and filters, preventing bottlenecks.  

