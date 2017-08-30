---
layout: default
title: Hardware
---

# Hardware to Play ROCm


#### ROCm Platform Supports Two Graphics Core Next (GCN) GPU Generations

* GFX8: Radeon RX 480,Radeon RX 470,Radeon RX 460,R9 Nano,Radeon R9 Fury,Radeon R9 Fury X Radeon Pro WX7100, FirePro S9300 x2
* Radeon Vega Frointer Edition
* Radeon Instinct: MI6, MI8, and MI25 

##### Supported CPU

ROCm Platform leverages modern CPUs supporting PCI Express 3.0 or greater, exploiting advanced capabilities including PCIe Atomics (Fetch and Add, Compare and Swap, Unconditional Swap, AtomicOp Completion). To find out more; https://github.com/RadeonOpenCompute/RadeonOpenCompute.github.io/blob/master/ROCmPCIeFeatures.md
 
To support ROCm programming model, the GPUs are installed in PCIe slots with PCI Express 3.0 or higher capabilities with transfer rates of 8.0 GT/s in either x16 or x8 lanes. The system configuration can have the PCIe slots directly on CPU’s root port or a PCIe switch port. The CPU root must indicate PCIe AtomicOp Completion capabilities and any intermediate switch must indicate PCIe AtomicOp Routing capabilities.
 
Note that the physical PCIe slot size does not guarantee support for ROCm. We have reports of few consumer motherboards which support physical x16 PCIe slots, but the PCIe connector is electrically connected as x4 PCIe Express 2.0 from the Southbridge. Since the PCIe slot connector matters to the GPU, care must be taken to not place them in on motherboards configured this way.
 
ROCm Kernel driver logs if ROCm capable GPUs are installed on system that does not support PCIe atomics. 

Example text from kernel log:
kfd: skipped device 1002:7300, PCI rejects atomics
 

When you install your GPU's Make sure you install them on real PCIexpress Gen3 (PCIe Gen3) x16 or x8 lanes directly on CPU's Root I/O controller or a PCIe Switch directly attached to the CPU's Root I/O controller. We have seen many issue with Consumer motherboard which support Physical x16 Connectors, but the connector is electrically connected as PCIe Gen2 x4, if you see this it is typically hanging off the Southbridge PCIe I/O controller. If your motherboard is configured this way please do not use this connector for your GPU.

###### Current CPU which support PCIe Gen3 + PCIe Atomics are: 

* AMD
  * RYZEN CPU
  * RYZEN Threadripper
  * EPYC Server CPU 

* INTEL 
  * Xeon E5/E7 v3 or newer CPU's 
  * Xeon E3 v3 or newer CPU's
  * Core i7 v3, Core i5 v3, Core i3 v3 or newer CPU's  
  
 * Cavium Thunder X Server Processor </li>

###### Curently Not supported 
* AMD Carrizo and Kaveri APU with external GPU Attached are not supported by ROCm 
* Thunderbolt 1 and 2 enabled GPU's are not Support by ROCm.  Thunderbolt 1 &amp; 2 are PCIe Gen2 based.

AMD Carrizo based APU have limited support due to OEM &amp; ODM's Carrizo enabled Laptop, All In One System and Desktop system had inconsistency in supporting the correct System BIOS configurations for ROCm driver enablement. Before you buy a Carrizo system to run ROCm.  You should check the SBIOS to see if has an option to enable IOMMUv2. If this is enabled, next we need test for the correct CRAT Table support to properly configure the driver.  

