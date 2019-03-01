---
layout: default
title: Hardware
---

# Hardware to Play ROCm

### Officially Supported GPUs
Because the ROCm Platform has a focus on particular computational domains, we offer official support for a selection of AMD GPUs that are designed to offer good performance and price in these domains. This section details the GPUs that ROCm Supports.

#### GFX8 GPUs
ROCm offers support for three chips from AMD's "gfx8" generation of GPUs. Note that these GPUs all require a host CPU and platform with PCIe 3.0 with support for PCIe atomics. This is detailed further in the following section on CPU requirements.

* "Fiji" chips, which include the following GPUs:
  * AMD Radeon R9 Fury
  * AMD Radeon R9 Nano
  * AMD Radeon R9 Fury X
  * AMD Radeon Pro Duo (Fiji)
  * AMD FirePro S9300 X2
  * AMD Radeon Instinct MI8
* "Polaris 10" chips, including the following GPUs:
  * AMD Radeon RX 470
  * AMD Radeon RX 480
  * AMD Radeon RX 570
  * AMD Radeon RX 580
  * AMD Radeon Pro Duo (Polaris)
  * AMD Radeon Pro WX 5100
  * AMD Radeon Pro WX 7100
  * AMD Radeon Instinct MI6
* "Polaris 11" chips, including the following GPUs:
  * AMD Radeon RX 460
  * AMD Radeon RX 560
  * AMD Radeon Pro WX 4100
* "Polaris 12" chips (also known as "Lexa"), including the following GPUs:
  * AMD Radeon RX 540
  * AMD Radeon RX 550
  * AMD Radeon Pro WX 2100
  * AMD Radeon Pro WX 3100

#### GFX9 GPUs
ROCm offers support for two chips from AMD's most recent "gfx9" generation of GPUs. As of ROCm 1.8, we have enabled a mode of operation that does not require PCIe atomics on these GPUs, at the expense of lower performance. In ROCm 1.8.x, if you want to run any of these gfx9 GPUs on a system that does not support PCIe 3.0 with atomics, please set the environment variable `HSA_ENABLE_SDMA=0`. This is not required in ROCm 1.9.x.

* "Vega 10" chips, including the following GPUs:
  * AMD Radeon RX Vega 56
  * AMD Radeon RX Vega 64
  * AMD Radeon Vega Frontier Edition
  * AMD Radeon Pro WX 8200
  * AMD Radeon Pro WX 9100
  * AMD Radeon Pro V340
  * AMD Radeon Pro V340 MxGPU
  * AMD Radeon Instinct MI25
  * Note that ROCm does *not* support the Radeon Pro SSG
* "Vega 7nm" chips, including the following GPUs:
  * AMD Radeon VII
  * AMD Radeon Instinct MI50
  * AMD Radeon Instinct MI60

### GPUs that are enabled, but which AMD does not officially support
ROCm is a collection of software ranging from drivers and runtimes to libraries and developer tools.
Some of this software may work with more GPUs than the "officially supported" list above, though AMD does not make any official claims of support for these devices on the ROCm software platform.

#### GFX7 GPUs
ROCm has code to enable one chip from AMD's "gfx7" generation of GPUs. These GPUs do not require PCIe atomics.

* "Hawaii" chips, including the following GPUs:
  * AMD Radeon R9 290
  * AMD Radeon R9 290X
  * AMD Radeon R9 295X2
  * AMD Radeon R9 390
  * AMD Radeon R9 390X
  * AMD FirePro W8100
  * AMD FirePro W9100
  * AMD FirePro S9150
  * AMD FirePro S9170

#### The iGPU in AMD APUs

The following APUs are not fully supported by the ROCm stack.

* "Carrizo" and "Bristol Ridge" APUs
* "Raven Ridge" APUs

These APUs are enabled in  the upstream Linux kernel drivers and the ROCm [Thunk](https://github.com/RadeonOpenCompute/ROCT-Thunk-Interface).
Support for these APUs is enabled in the [ROCm OpenCL runtime](https://github.com/RadeonOpenCompute/ROCm-OpenCL-Runtime).
However, support for them is not enabled in our [HCC compiler](https://github.com/RadeonOpenCompute/hcc), [HIP](https://github.com/ROCm-Developer-Tools/HIP), or the ROCm libraries.
In addition, because ROCm is currently focused on discrete GPUs, AMD does not make any claims of continued support in the ROCm stack for these integrated GPUs.

In addition, these APUs may may not work due to OEM and ODM choices when it comes to key configurations parameters such as inclusion of the required CRAT tables and IOMMU configuration parameters in the system BIOS.
As such, APU-based laptops, all-in-one systems, and desktop motherboards may not be properly detected by the ROCm drivers.
You should check with your system vendor to see if these options are available before attempting to use an APU-based system with ROCm.

### GPUs that are known not to work with ROCm
As of ROCm 1.9, the following GPUs are known *not to work* with ROCm because the basic drivers required for ROCm, such as `amdkfd` do not include support for them.
* Any pre-GCN AMD GPU
  * This includes "Evergreen" and "Northern Islands" GPUs, and "Trinity"/"Richland" APUs
* Any GPU from the "Southern Islands" (gfx6) generation of GCN GPUs, including the following chips:
  * "Cape Verde"
  * "Pitcairn"
  * "Tahiti"
* Any "Sea Islands" (gfx7) GPU besides "Hawaii", including:
  * "Bonaire" and "Oland"
* "Iceland" chips (gfx802), also known as "Topaz".
* AMD Radeon Vega M
* AMD "Kaveri" and "Godavari" APUs

The following GPU is known *not to work* with ROCm 1.9 and before because of a bug in the [Thunk](https://github.com/RadeonOpenCompute/ROCT-Thunk-Interface). Because of this runtime bug, the [HCC compiler](https://github.com/RadeonOpenCompute/hcc) has chosen to disable compilation for this class of GPUs as well, and thus none of the ROCm libraries are built for this GPU.
* "Tonga" chips, including the following GPUs:
  * Radeon R9 285
  * Radeon R9 380
  * Radeon R9 380X
  * FirePro W7100
  * FirePro S7150
  * FirePro S7100X
  * FirePro S7150x2

##### Supported CPUs

As described above, GFX8 and GFX9 GPUs require PCI Express 3.0 with PCIe atomics in the default ROCm configuration.
The ROCm Platform leverages these advanced capabilities ( including PCIe atomic Fetch and Add, Compare and Swap, Unconditional Swap, AtomicOp Completion) to allow features such as user-level submission of work from the host to the GPU.  To find out more; [PCIe Atomics and Large Bar Overview](/ROCmPCIeFeatures.md)
 
As such, by default ROCm requires that these GPUs be installed in PCIe slots with PCI Express 3.0 or higher capabilities with transfer rates of 8.0 GT/s in either x16 or x8 lanes. The system configuration can have the PCIe slots directly on CPU's root port or a PCIe switch, but everything between the CPU and the GPU must support atomics. The CPU root must indicate PCIe AtomicOp Completion capabilities and any intermediate switch must indicate PCIe AtomicOp Routing capabilities.

PCIe root port must report and support
* 32-bit AtomicOp Completer Supported = 1
* 64-bit AtomicOp Completer Supported = 1
 
All PCIe switches between GPU End Point and Root Point must report and support
* AtomicOp Routing Supported = 1
 
Note that the physical PCIe slot size does not guarantee support for ROCm. Some motherboards have physical x16 PCIe slots, but the PCIe connector is electrically connected as PCIe Express 2.0 to the southbridge. Since the PCIe slot connector matters to the GPU, care must be taken to not place them in on motherboards configured this way.
 
The ROCm kernel driver logs if ROCm capable GPUs are installed on system that does not support PCIe atomics. 

Example text from kernel log:
```
kfd: skipped device 1002:7300, PCI rejects atomics
```

###### Current CPUs with support PCIe 3.0 + PCIe Atomics: 

* AMD
  * Ryzen CPUs (Family 17h Model 01h-0Fh -- previously code-named Zen) such as:
    * Ryzen 3 1300X
    * Ryzen 3 2300X
    * Ryzen 5 1600X
    * Ryzen 5 2600X
    * Ryzen 7 1800X
    * Ryzen 7 2700X
  * Ryzen APUs (Family 17h Model 10h-1Fh -- previously code-named Raven Ridge) such as:
    * Athlon 200GE
    * Ryzen 5 2400G
    * Note that the integrated GPU in these devices is *not* guaranteed to work with ROCm.
  * Ryzen Threadripper Workstation CPUs (Family 17h Model 01h-0Fh -- previously code-named Zen) such as:
    * Ryzen Threadripper 1950X
    * Ryzen Threadripper 2990WX
  * EPYC Server CPUs (Family 17h Model 01h-0Fh -- previously code-named Zen) such as:
    * Epyc 7551P
    * Epyc 7601

* INTEL 
  * Intel Core i3, i5, and i7 CPUs from "Haswell" and beyond. This includes:
    * "Haswell" CPUs such as the Core i7 4790K
    * "Broadwell" CPUs such as the Core i7 5775C
    * "Skylake" CPUs such as the Core i7 6700K
    * "Kaby Lake" CPUs such as the Core i7 7740X
    * "Coffee Lake" CPUs such as the Core i7 8700K
  * Xeon CPUs from "v3" and newer
  * Some models of "Ivy Bridge-E" processors
  
###### Currently NOT supported 
The following CPUs *do not* support PCIe 3.0 atomics, and as such are not supported ROCm host platforms for gfx8 GPUs. gfx9 GPUs may work with these platforms, though they may run slower due to the lack of PCIe atomics.

* AMD Phenom CPUs
* AMD FX CPUs
* AMD Opteron CPUs
* AMD Kaveri APUs
* AMD Carrizo APUs
* Intel CPUs that were released before "Haswell" and "Ivy Bridge-E"

In addition, connecting gfx8 GPUs to the host through Thunderbolt 1 or Thunderbolt 2 adapters is not supported because these are based on PCIe 2.0.
