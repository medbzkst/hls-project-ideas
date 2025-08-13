# RGB to Greyscale Conversion

## Introduction  
RGB to greyscale conversion is a technique used to transform a colored image (in the RGB color model) to grayscale. Each pixel's red, green, and blue components are combined into a single intensity value that represents the pixel's brightness, discarding color information. This is essential for simplifying images for tasks like edge detection, object recognition, or reducing computational load in machine learning models.

For more details, have a look at https://en.wikipedia.org/wiki/Grayscale.

## Applications
- **Computer vision** (simplified input for edge detection, facial recognition)  
- **Image processing** (preprocessing step in image filtering, segmentation)  
- **Video processing** (reducing the data size for faster processing)  
- **Machine learning** (grayscale images as inputs for neural networks)

## Why Accelerate RGB to Greyscale Conversion on FPGA?  
- **High-throughput requirement**: Large images must be processed quickly, which is made more efficient with FPGA's parallel processing capabilities.
- **Low-latency execution**: Real-time video processing applications benefit from fast conversions.
- **Simplified design**: FPGA hardware is well-suited to handle pixel-by-pixel operations like converting RGB to greyscale efficiently.

## An HLS Design Perspective 
- **Dataflow pipelining (`#pragma HLS dataflow`)** enables continuous processing of image pixels.
- **Loop unrolling (`#pragma HLS unroll`)** helps process multiple pixels simultaneously.
- **Memory partitioning (`#pragma HLS array_partition`)** ensures optimized access to image pixel values, reducing memory bottlenecks during processing.

