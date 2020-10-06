####Welcome to the ROCm Platform

We are excited to present to you the ROCm the first Open Source HPC/Ultrascale class GPU computing platform which is also programming language independent. We are bringing the UNIX philosophy of choice, minimalist, modular software development to GPU Computing. The new ROCm foundation lets you choose or even develop your tools and language runtime needed to develop your application.

ROCm built for scale; it supports multi-GPU computing in server node and out of server node communication via RDMA. We also focused on simplifying the stack were RDMA Peer Sync support is built directly into the driver.  

ROCm has a rich system runtime with the key features needed to support large scale application, compiler, and language runtime development:

* At the core is the Heterogeneous System Architecture ("HSA") Runtime API
 * Multi-GPU Coarse-grain Shared Virtual Memory 
 * Process Concurrency & Preemption
 * Large Memory Allocations 
 * HSA Signals and Atomics
 * User Mode Queues and DMA
* Standardized loader and Code Object Format
 * Dynamics and Offline Compilation Support
* Peer to Peer Multi-GPU with RDMA Support
* Profiler Trace and Event Collection API 
* Systems Management API and Tools

We are also delivering a rich open source llvm based compiler foundation with native GCN ISA code generation.  This foundation will all you to develop commercial quality development tools and a framework to explore GPU computing language development. 

* LLVM Compiler Foundation 
 * LLVM Compiler with GCN Native Compilation 
 * Supports GCN Assembler and Disassembler
 * Fully Upstream in the LLVM source repository  
 
 
Building on this is rich system runtime is a set of GPU Enabled Programing Languages to allow to focus on your application idea in familiar application development environment. The ROCm platform initially is supporting C, C++ and Python based GPU enabled programming solutions. 

Heterogeneous Compute Compiler (HCC) supports C11 & C++ 11/14 with llvm code generation backend for AMD x64 and GCN ISA. The HCC Compiler has three language persona. 

* Single Source C++ 11/14 with Parallel Standard Template Library (STL)
* HIP is  C++ GPU Kernel Language with C-Style Language Runtime that to ease conversion of CUDA applications into portable C++ code. 
* OpenMP 3.1 for CPU based programs that can integrate HIP or C++ 11/14 based GPU acceleration 

OpenCL 1.2+ Compiler and Language Runtime release will be made available in the Fall, which will support the new native GCN ISA compiler and also integrated into the new capabilities in the ROCm system runtime.  

With the explosion of use of Python in application programming and Data Analytics. We are bringing Continuum Analytics Anaconda with Numba Acceleration to ROCm. Numba helps you accelerate array-oriented and math-heavy Python codes. Kernels compiled with Numba also have direct access to NumPy arrays.   

To give you deeper visibility into ROCm platform are developing the fundamental profiling and debugging tools( GDB Debugger, ROCm Profiler). 

To accelerate the speed at which you can build your application, we are bringing a comprehensive set of math libraries ( BLAS, FFT, Sparse, RNG) and programming frameworks( RAJA, Kokkos, CHARM++, HPX) to ROCm as well. 

The frontiers of where you take ROCm is just beginning,  we look forward working with you to improve the platform to help you drive the exploration of your application domains.  We know we have opened the door to unique heterogeneous computing applications and a new opportunity to explore what possible with heterogeneous computing.  
