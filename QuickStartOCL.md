---
layout: default
title: Quickstart OpenCL 
---

# Overview

### ROCm 1.6 introduces big updates to our OpenCL compiler and runtime implementation -- built on top of the ROCm software stack!

#### This developer release includes the following:

* OpenCL 2.0 compatible kernel language support with OpenCL 1.2 compatible runtime
* OpenCL compiler also has assembler and disassembler support,  inline assembly support is now in place. 
* Big improvements in the base compiler as we roll in new optimization for application in new Native LLVM code generator. 
* We made our base compiler intrinsics source code available
  * OCML https://github.com/RadeonOpenCompute/ROCm-Device-Libs/blob/master/doc/OCML.md
  * Source code for the Intrinsic https://github.com/RadeonOpenCompute/ROCm-Device-Libs/tree/master/opencl/src
* Supports offline ahead of time compilation and in-process/in-memory compilation.
* Binary Package support for Ubuntu  16.04 and Fedora 24

#### Quickstart Instructions

#### Here's a simple workflow to get you quickly up and running with OpenCL on ROCm --

##### Install the ROCm OpenCL implementation (assuming you already have the 'rocm' package installed):

```shell
sudo apt-get install rocm-opencl-dev
```
Set an environment variable that points to the installation directory for OpenCL:
```shell
export OPENCL_ROOT=/opt/rocm/opencl
```
For a sample OpenCL application, let's use a simple vector-add example from the University of Bristol's very nice "Hands On OpenCL" lectures.

```shell
git clone https://github.com/HandsOnOpenCL/Exercises-Solutions.git

cd Exercises-Solutions/Exercises/Exercise02/C

make \
  CCFLAGS="-I$OPENCL_ROOT/include/opencl1.2 -O3 -DDEVICE=CL_DEVICE_TYPE_DEFAULT" \
  LIBS="-L$OPENCL_ROOT/lib/x86_64 -lOpenCL -lm"

./vadd
```
##### That's it!  Super easy.

#### Related Resources

ROCm Developer website will have more information: http:/rocm.github.io

University of Bristol's "Hands On OpenCL" course webpage:  https://handsonopencl.github.io/
