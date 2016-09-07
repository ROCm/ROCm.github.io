---
layout: default
title: ROCm Languages
---

## ROCm, Lingua Franca,  C++, OpenCL and Python

The open-source ROCm stack offers multiple programming-language
choices. The goal is to give you a range of tools to help solve the
problem at hand. Here, we describe some of the options and how to
choose among them.

### HCC: Heterogeneous Compute Compiler

What is the Heterogeneous Compute (HC) API? It’s a C++ dialect with
extensions to launch kernels and manage accelerator memory. It closely
tracks the evolution of C++ and will incorporate parallelism and
concurrency features as the C++ standard does. For example, HC
includes early support for the C++17 Parallel STL. At the recent ISO
C++ meetings in Kona and Jacksonville, the committee was excited about
enabling the language to express all forms of parallelism, including
multicore CPU, SIMD and GPU. We’ll be following these developments
closely, and you’ll see HC move quickly to include standard C++
capabilities.

The Heterogeneous Compute Compiler (HCC) provides two important
benefits:

*Ease of development*

 * A full C++ API for managing devices, queues and events
 * C++ data containers that provide type safety,
   multidimensional-array indexing and automatic data management
 * C++ kernel-launch syntax using parallel_for_each plus C++11 lambda
   functions
 * A single-source C++ programming environment---the host and source
   code can be in the same source file and use the same C++ language;
   templates and classes work naturally across the host/device
   boundary
 * HCC generates both host and device code from the same compiler, so
   it benefits from a consistent view of the source code using the
   same Clang-based language parser

*Full control over the machine*

 * Access AMD scratchpad memories (“LDS”)
 * Fully control data movement, prefetch and discard
 * Fully control asynchronous kernel launch and completion
 * Get device-side dependency resolution for kernel and data commands (without host involvement)
 * Obtain HSA agents, queues and signals for low-level control of the architecture using the HSA Runtime API
 * Use [direct-to-ISA](https://github.com/RadeonOpenCompute/HCC-Native-GCN-ISA) compilation

#### When to Use HC

Use HC when you're targeting the AMD ROCm platform: it delivers an
easy-to-program, single-source C++ environment without compromising
performance or control of the machine.

### HIP: Heterogeneous-Computing Interface for Portability

What is Heterogeneous-Computing Interface for Portability (HIP)? It’s
a C++ dialect designed to ease conversion of Cuda applications to
portable C++ code. It provides a C-style API and a C++ kernel
language. The C++ interface can use templates and classes across the
host/kernel boundary.

The Hipify tool automates much of the conversion work by performing a
source-to-source transformation from Cuda to HIP. HIP code can run on
AMD hardware (through the HCC compiler) or Nvidia hardware (through
the NVCC compiler) with no performance loss compared with the original
Cuda code.

Programmers familiar with other GPGPU languages will find HIP very
easy to learn and use. AMD platforms implement this language using the
HC dialect described above, providing similar low-level control over
the machine.

#### When to Use HIP

Use HIP when converting Cuda applications to portable C++ and for new
projects that require portability between AMD and Nvidia. HIP provides
a C++ development language and access to the best development tools on
both platforms.

### OpenCL™: Open Compute Language

What is OpenCL? It’s a framework for developing programs that can
execute across a wide variety of heterogeneous platforms. AMD, Intel
and Nvidia GPUs support version 1.2 of the specification, as do x86
CPUs and other devices (including FPGAs and DSPs). OpenCL provides a C
run-time API and C99-based kernel language.

When to Use OpenCL

Use OpenCL when you have existing code in that language and when you
need portability to multiple platforms and devices. It runs on
Windows, Linux and Mac OS, as well as a wide variety of hardware
platforms (described above).

### Anaconda Python With Numba

What is Anaconda? It’s a modern open-source analytics platform powered
by Python. Continuum Analytics, a ROCm platform partner,  is the
driving force behind it. Anaconda delivers high-performance
capabilities including acceleration of HSA APUs, as well as
Boltzmann-enabled discrete GPUs via Numba. It gives superpowers to the
people who are changing the world.

### Numba

Numba gives you the power to speed up your applications with
high-performance functions written directly in Python. Through a few
annotations, you can just-in-time compile array-oriented and
math-heavy Python code to native machine instructions - offering
performance similar to that of C, C++ and Fortran -without having to
switch languages or Python interpreters.

Numba works by generating optimized machine code using the LLVM
compiler infrastructure at import time, run time or statically
(through the included Pycc tool). It supports Python compilation to
run on either CPU or GPU hardware and is designed to integrate with
Python scientific software stacks, such as NUMpy.

#### When to Use Anaconda

Use Anaconda when you’re handling large-scale data-analytics,
scientific and engineering problems that require you to manipulate
large data arrays.

### Wrap-Up

From a high-level perspective, ROCm delivers a rich set of tools that
allow you to choose the best language for your application.

 * HCC (Heterogeneous Compute Compiler) supports HC dialects
 * HIP is a run-time library that layers on top of HCC (for AMD ROCm platforms; for Nvidia, it uses the NVCC compiler)
 * Soon to offer native GCN ISA compiler support:
    * OpenCL 1.2+
    * Anaconda (Python) with Numba

All are open-source projects, so you can employ a fully open stack
from the language down to the metal. AMD is committed to providing an
open ecosystem that gives developers the ability to choose; we are
excited about innovating quickly using open source and about
interacting closely with our developer community. More to come soon!
