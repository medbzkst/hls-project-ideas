# 1024‑Point Streaming FFT for OFDM/SDR

## Application
Fast Fourier Transform (FFT) is a core operation in wireless communications, especially in OFDM-based physical layers and software-defined radio (SDR) systems. Streaming, high-throughput FFTs enable real-time spectrum analysis, modulation/demodulation, and signal processing for applications such as 5G, Wi-Fi, and cognitive radio.

## Context
FFT/IFFT is central to OFDM PHY and spectrum analysis.

## Objective
Build a **pipelined radix‑2/4** 1024‑point complex FFT with AXI‑Stream I/O and cyclic‑prefix (CP) add/remove.

## Scope & Partitioning
- **PS:** Frame builder/scheduler; test vector generation; golden via NumPy/FFTW.
- **PL:** Butterfly pipeline (II=1), twiddle ROMs, scaling per stage (block‑floating), optional CP module.

## Data types
12–16‑bit fixed‑point IQ; block‑floating scaling; report overflow counters.

## Constraints
Single core reused; twiddles in BRAM; latency ~O(N log N) cycles; optional windowing.

## Inputs/Outputs
- **Input:** Streams of length‑1024 complex frames
- **Output:** FFT outputs (or IFFT) with correct ordering and scaling

## Baseline
PS NumPy `np.fft.fft` on the same frames.

## Targets
- **SNR/NRMSE:** ≥ 60 dB vs float reference (with fixed‑point tuning).
