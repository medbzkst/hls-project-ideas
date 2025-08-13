# Line‑Buffered Bilinear Resizer for Vision Pre‑processing

## Application
Bilinear image resizing is a common pre-processing step in computer vision pipelines, especially for deep learning models that require fixed-size inputs. Efficient hardware-based resizing with color conversion and normalization supports real-time video analytics, surveillance, and edge AI deployments.

## Context
Video analytics need resizing from 1080p/720p to model input (e.g., 224×224 or 640×640).

## Objective
Implement **bilinear resize** with on‑the‑fly color convert (YUV→RGB) and normalization; stream in/out.

## Scope & Partitioning
- **PS:** Decode frames (OpenCV/ffmpeg), allocate DMA buffers, verify results.
- **PL:** 3 line buffers per plane, fixed‑point bilinear weights, optional per‑channel mean/std normalization.

## Constraints
1–2 pixels/clk; support at least 1080p→224² @ 30 fps; line buffers in BRAM.

## Inputs/Outputs
- **Input:** RGB or YUV frames
- **Output:** Resized, normalized frames/tensors

## Baseline
PS OpenCV `resize` + `cvtColor`.

## Targets
- **PSNR:** ≥ 40 dB vs OpenCV bilinear on a test set
