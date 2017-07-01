---
layout: default
title: Deep Learning
---
# Deep Learning on ROCm 

Announcing our new Foundation for Deep Learning acceleration  MIOpen 1.0 which introduces support for Convolution Neural Network acceleration — built to run on top of the ROCm software stack!

## This release includes the following:

Deep Convolution Solvers  optimized for both forward and backward propagation
Optimized Convolutions including Winograd and FFT transformations
Optimized GEMM’s for Deep Learning
Pooling, Softmax, Activations, Gradient Algorithms Batch Normalization, and LR Normalization
MIOpen describes data as 4-D tensors ‒ Tensors 4D NCHW format
Support for OpenCL and HIP enabled frameworks
MIOpen Driver enables to testing forward/backward network of any particular layer in MIOpen.
Binary Package support for Ubuntu  16.04 and Fedora 24
Source code at https://github.com/ROCmSoftwarePlatform/MIOpen

## The  ROCm 1.6 has prebuilt packages for MIOpen 

Install the ROCm MIOpen implementation (assuming you already have the ‘rocm’  and ‘rocm-opencl-dev” package installed):

### For just OpenCL development  
```shell
sudo apt-get install miopengemm miopen-opencl 
```   
### For HIP development
```shell
sudo apt-get install miopengemm miopen-hip
```     
### Or you can build from [source code](https://github.com/ROCmSoftwarePlatform/MIOpen) following the instructions at 
