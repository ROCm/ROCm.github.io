---
layout: default
title: ROCm Documentation
---

## ROCm Documentation

The ROCm documentation site is where we assemble quick-start guides, installation guides, programming guides, API reference documentation, tool documentation and whitepapers.

* [Beta Online ROCm Documentation](http://rocm-documentation.readthedocs.io/en/latest/index.html)

### ROCm Install  
* [ROCm Install Quick Start Guide](ROCmInstall.md)
* [ROCm Install FAQ](install_issues.md)
* [ROCm Supported Hardware](hardware.md) 
* [Quick Start OpenCL](QuickStartOCL.md)
* [ROCm Language Introduction](https://github.com/ROCm/ROCm.github.io/blob/master/languages.md)

#### [ROCm and AMDGPU Catalyst Driver Comparison](ROCmRadeonProcompare.md)

#### ROCr Run-Time Documentation 

* [HSA Runtime specification---HSA Foundation online documents](http://www.hsafoundation.com/html_spec11/HSA_Library.htm)
* [ROCr error codes](ROCmRTec.html)

#### AMDGPU LLVM Compiler 

* [Doucmentation for AMDGPU Code Generator in LVVM](http://llvm.org/docs/AMDGPUUsage.html)

#### HCC

* [HCC overview](https://github.com/RadeonOpenCompute/hcc/wiki)
* [How to use HCC and select a GPU device](https://github.com/RadeonOpenCompute/hcc/wiki#how-to-use-hcc)
* [HCC language API documentation](http://scchan.github.io/hcc/)
* [HC API: Moving Beyond C++ AMP for Accelerated GPU Computing](https://github.com/RadeonOpenCompute/hcc/blob/master/doc/markdown/Home.md)
* [HCC Saxpy example](https://gist.github.com/scchan/540d410456e3e2682dbf018d3c179008)

#### HIP

* [HIP porting guide: overview and
  how-to](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/blob/master/docs/markdown/hip_porting_guide.md)
* [HIP terminology comparison with OpenCL, Cuda, C++ AMP and HCC](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/blob/master/docs/markdown/hip_terms.md)
* [HIP run-time API overview and documentation
  (Doxygen)](http://gpuopen-professionalcompute-tools.github.io/HIP/)
* [HIP kernel-language overview](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/blob/master/docs/markdown/hip_kernel_language.md)
* [HIP FAQ](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/blob/master/docs/markdown/hip_faq.md)

#### OpenCL 

* [Quick Start for OpenCL](QuickStartOCL.md)
* ROCm support OpenCl 1.2 & 2.0 minus PIPES and Device Enqueue. 

#### GCN ISA, ROCm Object Format, ABI and Assembly Documentation 

* [GCN Architecture overview](https://www.amd.com/Documents/GCN_Architecture_whitepaper.pdf)
* [GCN Architecure crash course by Lala Mah](http://www.slideshare.net/DevCentralAMD/gs4106-the-amd-gcn-architecture-a-crash-course-by-layla-mah)
* [GFX7 GCN ISA Southern Islands manual---Hawaii ]( http://bit.ly/29t5aQP)
* [GFX8  GCN Version 3---Tonga, Fiji and Polaris ](http://amd-dev.wpengine.netdna-cdn.com/wordpress/media/2013/12/AMD_GCN3_Instruction_Set_Architecture_rev1.1.pdf)
* [AMD GPU-compute application binary interface (ABI) ](https://github.com/RadeonOpenCompute/ROCm-ComputeABI-Doc/blob/master/AMDGPU-ABI.md)
* [Documentation covering helper tools for ROCm GCN LLVM assembler](https://github.com/RadeonOpenCompute/LLVM-AMDGPU-Assembler-Extra/blob/master/README.md)
* [GCN float16](GCN_Float16.html)
* [ROC device library---Open Compute Math Library  intrinsics](https://github.com/RadeonOpenCompute/ROCm-Device-Libs/blob/master/doc/OCML.md)

#### MultiGPU Programing In-node P2P and Out of Node P2P 
[ROCm P2P Documentation and Solution for In-node P2P and Network RDMA based P2P](/ROCmMultiGPU.md)

#### Development Tools 

* [ROCm profiler: overview and how-to](http://gpuopen.com/getting-up-to-speed-with-the-codexl-gpu-profiler-and-radeon-open-compute/)
* [GPU Performance API (GPUPerfAPI), including access to performance counters](https://github.com/GPUOpen-Tools/GPA/blob/master/Doc/GPUPerfAPI-UserGuide.pdf)  
* [ROCm GDB debugger: overview and how-to](https://github.com/RadeonOpenCompute/ROCm-Debugger/blob/master/TUTORIAL.md)
* [ROCm compiler development: foundation for creating your own compiler](ROCmCompilerKit.html)

#### MIOpen

* [MIOpen Documentation](https://rocmsoftwareplatform.github.io/MIOpen/doc/html/) 
* [MIOpen GEMM - Deep Learning Optimized Gemm Library](https://rocmsoftwareplatform.github.io/MIOpenGEMM/doc/html/) 

#### DevOps and System Management 

* [ROCm system-management interface (SMI) documentation](https://github.com/RadeonOpenCompute/ROC-smi/blob/master/README.md)
* [ROCm Docker: setup and how-to](https://github.com/RadeonOpenCompute/ROCm-docker/blob/master/README.md)
* [ROCm use of PCIe Atomics and PCIe BAR overivew](ROCmPCIeFeatures.md)


