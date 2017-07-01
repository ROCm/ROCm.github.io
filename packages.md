---
layout: default
title: ROCm Optimized Applications and Libraries
---

#### ROCm Install 
You can perform a simplified ROCm install using our repository server. The package installs the driver, run time, HCC compiler and HIP language run time, as well as test apps to get you ready to start development in about 5&ndash;10 minutes. 
* [ROCm Install Instructions] (ROCmInstall.md)
* [ROCm Instal FAQ](install_issues.md) 


#### Source-Code Repositories for Kernel Driver + Thunk + Run Time

* [ROCk](https://github.com/RadeonOpenCompute/ROCK-Kernel-Driver) Base Kernel Driver 
* [ROCr](https://github.com/RadeonOpenCompute/ROCR-Runtime) User Space System Runtime 

#### Peer-to-Peer RDMA Source


[ROCnRDMA](https://github.com/RadeonOpenCompute/ROCnRDMA)
[RDMA performance test](https://github.com/RadeonOpenCompute/rdma-perftest)

### Development Tools

#### HCC Compiler

* [HCC compiler source](href="https://github.com/RadeonOpenCompute/hcc)
* [HCC Clang source](https://github.com/RadeonOpenCompute/hcc-clang)

#### HIP

* [HIP run time and tools for porting Cuda applications with HCC](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP)
* [HIP examples](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP-Examples)
* [Mixbench;a good test to understand the effective performance of a GPU across arithmetic intensities](https://github.com/ekondis/mixbench)

#### LLVM Source for GCN ISA Compiler

* [LLVM source code for native GCN ISA code generation](https://github.com/RadeonOpenCompute/llvm)
* [ROCm device-library compiler intrinsics with Open Compute Math Library and Open Compute kernel language](https://github.com/RadeonOpenCompute/ROCm-Device-Libs)


#### Continuum Analytics: Python Distribution With ROCm Acceleration

* [Anaconda® with Numba acceleration](http://numba.pydata.org/numba-doc/latest/index.html)


### GCN ISA Assembly Tools

Our LLVM code generator now supports the GCN ISA disassembler and assembler. 

* [Helper tools for the GCN assembler](https://github.com/RadeonOpenCompute/LLVM-AMDGPU-Assembler-Extra)

### GCN ISA Manual


* [GCN Version 3 ISA manual&mdash;Fiji, Tonga](http://amd-dev.wpengine.netdna-cdn.com/wordpress/media/2013/12/AMD_GCN3_Instruction_Set_Architecture_rev1.1.pdf)
* [GCN ISA Southern Islands manual;Hawaii](http://bit.ly/29t5aQP)

### Debugger

* [ROCm debugger binary build](https://github.com/RadeonOpenCompute/ROCm-Debugger)
* [ROCm GDB source code](https://github.com/RadeonOpenCompute/ROCm-GDB)
* [ROCm GPU debugger SDK;ROCm debug run time that services GBD](https://github.com/RadeonOpenCompute/ROCm-GPUDebugSDK)

### Profiling Tools


* [RCP command-line profiler](https://github.com/GPUOpen-Tools/RCP)
* [CodeXL;a CPU and GPU profiler in one tool (now fully open source under the BSD license)](https://github.com/GPUOpen-Tools/CodeXL)
* [GPUPerfAPI](https://github.com/GPUOpen-Tools/GPA)

### Libraries


#### Math Libraries

* [rocBLAS](https://github.com/ROCmSoftwarePlatform/rocBLAS)
* [rocFFT](https://github.com/ROCmSoftwarePlatform/rocFFT)
* [Tensile](https://github.com/ROCmSoftwarePlatform/Tensile)

* [Egien C++ Math Library with HIP Based GPU Acceleration](https://github.com/ROCmSoftwarePlatform/hipeigen) 

* [clBLAS](https://github.com/clMathLibraries/clBLAS)
* [clFFT](https://github.com/clMathLibraries/clFFT)
* [clSparse](https://github.com/clMathLibraries/clSPARSE)
* [clRNG](https://github.com/clMathLibraries/clRNG)

* [HcBLAS optimized for Torch7](https://github.com/ROCmSoftwarePlatform/hcBLAS)

  * BLAS Level 3: SGEMM, DGEMM, CGEMM 
  * BLAS Level 2: sgemv, dgemv, sger 
  * BLAS level 1: sasum, dasum, saxpy, scopy, dcopy, Sdot, Ddot, sscal, dscall

* [HcFFT](https://github.com/ROCmSoftwarePlatform/hcFFT)
* [HcRNG](https://github.com/ROCmSoftwarePlatform/hcRNG)


