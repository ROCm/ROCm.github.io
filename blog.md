---
layout: default
title: ROCm Blog
---

# ROCm Blog Roll

### ROCm Device Libraries Now Available!
We are pleased to announce fully open-source bitcode device libraries for the ROCm platform.

The following libraries are available:

* Open Compute Math Library (OCML)—contains 250+ optimized math functions for single, double and half precision. See the OCML documentation for a list of currently supported functions.
* Open Compute Kernel Library (OCKL)—contains many useful functions, including work-item/workgroup functions, integer optimization operations and wavefront reduce algorithms. It also serves as a foundation for the built-in library of the OpenCL-enabled compiler.
* Compiler built-in library to support OpenCL.
* Compiler built-in library for the HC mode of the Heterogeneous Compute Compiler (HCC).
* OCLC libraries—enable fine-grain control over library modes (such as relaxed math).
* IRIF—interface library to AMD GPU back end.

The libraries are intended for language and run-time implementors. They work with the open-source AMD GPU LLVM back end on GCN architectures and link to user bitcode through the LLVM linker before code generation.

ROCm-Device-Libs is currently under development, so we expect many improvements. As always, contributions and other feedback are welcome.

### Quickly Access ROCm GPU Performance Counters via Radeon Compute Profiler
You can get the list of available counters by running the following command:

```shell
./rcprof --list
```

To save the counter list to a file, use
```shell
./rcprof --list --outputfile counters.txt
```
Next, specify the set of counters using the following command:
```shell
./rcprof --hsapmc --counterfile counters.txt
```
"counters.txt" should list one counter name per line.

### HCC Adding Richer Array of Low-level Optimizations

* 24-bit integer multiply and multiply-add (__mul24 and __mad24)
* Intrinsics for ds_permute and ds_bpermute (__amdgcn_ds_permute and __amdgcn_ds_bpermute)
* Intrinsics for ds_swizzle (__amdgcn_ds_swizzle)
* Intrinsics for wave shift and rotate by one thread (__amdgcn_wave_*)
* Intrinsic for move dpp (__amdgcn_move_dpp)
* Example of HCC Fuctions

```C++ 
unsigned int hc::__activelaneid_u32 () __HC__ 
```

Get the number of earlier (in flattened work-item order) active work items in the same wavefront.

```C++ 
uint64_t hc::__activelanemask_v4_b64_b1 (unsigned int input) __HC__ 
```
Return a bit mask showing which active work items in the wavefront have a nonzero input.

``` C++ 
unsigned int hc::__activelanecount_u32_b1 (unsigned int input) __HC__ 
```

Count the number of active work items in the current wavefront that have a nonzero input.

``` C++ 
unsigned int hc::__activelanepermute_b32 (unsigned int src, unsigned int laneId, unsigned int identity, unsigned int useIdentity) __HC__ 
```

Permute the active work items in the wavefront.

```C++ 
int hc::__any (int predicate) __HC__ 
```

Evaluate the predicate for all active work items in the wavefront and return a nonzero value if and only if every predicate evaluates to a nonzero value.

```C++ int hc::__all (int predicate) __HC__ ```

Evaluate the predicate for all active work items in the wavefront and return a nonzero value if and only if any one predicate evaluates to a nonzero value.

```C++ 
uint64_t hc::__ballot (int predicate) __HC__ 
```

Evaluate the predicate for all active work items in the wavefront and return an integer whose Nth bit is set if and only if the predicate evaluates to a nonzero value for the Nth work item of the wavefront and the Nth work item is active.

```C++
C++ unsigned int hc::__shfl_xor (unsigned int var, int laneMask, int width=__HSA_WAVEFRONT_SIZE__) __HC__ 
```

[Find out more about these HCC fuctions.](http://scchan.github.io/hcc/hc_8hpp.html)

### It’s Time to ROC
<iframe width="560" height="315" src="https://www.youtube.com/embed/dnKDFci2x2Q" frameborder="0" allowfullscreen></iframe>
HPC User Forum in Tucson; Gregory Stoner from AMD presents It's Time to ROC and overivew on ROCm SOftware Platform.

