# Image Resizing 

## Introduction  
Image resizing involves altering the dimensions of an image, either by increasing or decreasing its width and height while maintaining the image quality as much as possible. This operation is commonly used in image processing applications where images must be prepared for display or further analysis.

For more details, have a look at https://en.wikipedia.org/wiki/Image_scaling.

## Applications
- **Image processing** (resize for display, filtering, and transformation)  
- **Computer vision** (input preprocessing for object detection, segmentation)  
- **Medical imaging** (resize images for enhanced analysis)  
- **Multimedia applications** (resize images for social media, web pages)

## Why Accelerate Image Resizing on FPGA?  
- **Parallel computation**: Image resizing involves repetitive pixel operations which can be **parallelized** effectively on FPGAs.
- **High-throughput processing**: Resizing large images, especially in real-time, can benefit from FPGA’s low-latency capabilities.
- **Memory access optimization**: FPGA designs can optimize pixel access patterns by using on-chip memory for better throughput and reduced bottlenecks.

## An HLS Design Perspective 
- **Dataflow pipelining (`#pragma HLS dataflow`)** allows parallel processing of pixel in tiles.
- **Loop unrolling (`#pragma HLS unroll`)** can help process multiple pixels simultaneously.
- **Memory partitioning (`#pragma HLS array_partition`)** optimizes access to image data by storing rows/columns in different memory banks for faster access.

