---
layout: default
title: Quickstart OpenCL 
---

# Overview

### The AMD ROCm Platform supports OpenCL as of ROCm 1.6!

#### As of ROCm 2.0, this includes the following:

* OpenCL 2.0 compatible kernel language support with OpenCL 1.2 compatible runtime
* OpenCL compiler also has assembler and disassembler support,  inline assembly support is now in place. 
* Big improvements in the base compiler as we roll in new optimization for application in new Native LLVM code generator. 
* We made our base compiler intrinsics source code available
  * OCML https://github.com/RadeonOpenCompute/ROCm-Device-Libs/blob/master/doc/OCML.md
  * Source code for the Intrinsic https://github.com/RadeonOpenCompute/ROCm-Device-Libs/tree/master/opencl/src
* Supports offline ahead-of-time compilation and in-process/in-memory compilation.
  * Offline compilation support can be easily accessed using the [clang-ocl](https://github.com/RadeonOpenCompute/clang-ocl) scripts. Theese scripts demonstrate how to call use AMD's LLVM-based compiler to make offline-compiled kernel binaries that can be loaded into programs using `clCreateProgramWithBinary()`

#### Quickstart Instructions

Here is a simple workflow to get you quickly up and running with OpenCL on ROCm.
First, a supported kernel driver is required to allow AMD's use-level ROCm software to access supported GPUs.
For many ROCm installations, this is the `rock-dkms` kernel driver package.
However, if you are using a newer kernel (depending on your GPU, this can be as early as 4.17), you can choose to use the upstream kernel driver and skip installing any ROCm-specific drivers.

##### Install the ROCm OpenCL Runtime

Once you have a working kernel driver, the following command can be used to install the ROCm OpenCL runtime on Ubuntu:

```shell
sudo apt-get install rocm-opencl
```

If you are using RHEL/CentOS, you can use the following command ionstead:
```shell
sudo yum install rocm-opencl
```

##### Test your OpenCL Installation

For a sample OpenCL application, let's use a simple vector-add example from the University of Bristol's very nice "Hands On OpenCL" lectures.

```shell
OPENCL_ROOT=/opt/rocm/opencl/
git clone https://github.com/HandsOnOpenCL/Exercises-Solutions.git

cd Exercises-Solutions/Exercises/Exercise02/C

make \
  CCFLAGS="-I$OPENCL_ROOT/include/ -O3 -DDEVICE=CL_DEVICE_TYPE_DEFAULT" \
  LIBS="-L$OPENCL_ROOT/lib/x86_64 -lOpenCL -lm"

./vadd
```

Note that your applications will need to include OpenCL headers when you compile it.
These can be found in `/opt/rocm/opencl/include/` in ROCm installations, and they are added by the `rocm-opencl-dev` (on Ubuntu) and `rocm-opencl-devel` (on RHEL/CentOS) packages.
These packages are also installed whenever you install `rocm-opencl`.

If you have previously built your applications on a system using the AMD APP SDK, you do not need to install anything else besides `rocm-opencl`.
You only need to set the `AMDAPPSDKROOT` environment variable to point towards `/opt/rocm/opencl/`.
Please do not install the AMD APPS DK along with ROCm OpenCL.
The former is designed for old drivers and may cause older versions of the OpenCL runtime to be instantiated.

Example 1 for AMDAPPSDKROOT
```shell
export AMDAPPSDKROOT=/opt/rocm/opencl 
```
Example 2 for AMDAPPSDK
```shell
export AMDAPPSDK=/opt/rocm/opencl
```
Where is clinfo? 
```shell
/opt/rocm/opencl/bin/x86_64/clinfo 
```

##### That's it!  Super easy.

#### Related Resources

ROCm Developer website will have more information: http:/rocm.github.io

University of Bristol's "Hands On OpenCL" course webpage:  https://handsonopencl.github.io/
