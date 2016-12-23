---
layout: default
title: ROCm Install
---

## Are You Ready to ROCK?
The ROCm Platform brings a rich foundation to advanced computing by seamlessly
 integrating the CPU and GPU with the goal of solving real-world problems.

On April 25th, 2016, we delivered ROCm 1.0 built around three pillars:

1) Open Heterogeneous Computing Platform (Linux(R) Driver and Runtime Stack), 
   optimized for HPC & Ultra-scale class computing;
   
2) Heterogeneous C and C++ Single Source Compiler, to approach computation 
   holistically, on a system level, rather than as a discrete GPU artifact;
   
3) HIP, acknowledging the need for freedom of choice when it comes to platforms
   and APIs for GPU computing.

Using our knowledge of the HSA Standards and, more importantly, the HSA
Runtime, we have been able to successfully extended support to the dGPU with
critical features for accelerating NUMA computation. As a result, the ROCK
driver is composed of several components based on our efforts to develop the
Heterogeneous System Architecture for APUs, including the new AMDGPU driver,
the Kernel Fusion Driver (KFD), the HSA+ Runtime and an LLVM based compilation
stack which provides support for key languages. This support starts with AMD’s
FIJI Family of dGPUs, and has expanded to include the Hawaii dGPU Family in ROCm
1.2. ROCm 1.3 further extends support to include the Polaris Family of ASICs.

#### Supported CPUs
The ROCm Platform leverages PCIe Atomics (Fetch ADD, Compare and SWAP, 
Unconditional SWAP, AtomicsOpCompletion).
[PCIe atomics](https://github.com/RadeonOpenCompute/RadeonOpenCompute.github.io/blob/master/ROCmPCIeFeatures.md)
are only supported on PCIe Gen3 Enabled CPUs and PCIe Gen3 Switches like
Broadcom PLX. When you install your GPUs make sure you install them in a fully
PCIe Gen3 x16 or x8 slot attached either directly to the CPU's Root I/O 
controller or via a PCIe switch directly attached to the CPU's Root I/O 
controller. In our experience many issues stem from trying to use consumer 
motherboards which provide Physical x16 Connectors that are electrically 
connected as e.g. PCIe Gen2 x4. This typically occurs when connecting via the 
Southbridge PCIe I/O controller. If you motherboard is part of this category,
please do not use this connector for your GPUs, if you intend to exploit ROCm.


Our GFX8 GPU's ( Fiji &  Polaris Family) use PCIe Gen 3 and PCIe Atomics. 

Current CPUs which support PCIe Gen3 + PCIe Atomics are: 
  * Intel Xeon E5 v3 or newer CPUs; 
  * Intel Xeon E3 v3 or newer CPUs; 
  * Intel Core i7 v3, Core i5 v3, Core i3 v3 or newer CPUs (i.e. Haswell family
  or newer).
  
Upcoming CPUs which will support PCIe Gen3 + PCIe Atomics are:
  * AMD Ryzen CPUs;
  * AMD Naples Server CPUs; 
  * Cavium Thunder X Server Processor. 

Our GFX7 GPUs Radeon R9 290, R9 390, AMD FirePro S9150, S9170 do not support or
take advantage of PCIe Atomics. However, we still recommend that you use a CPU
from the list provided above. 

#### Not Supported or Very Limited Support Under ROCm 
* We do not support ROCm with PCIe Gen 2 enabled CPUs such as the AMD Opteron,
Phenom, Phenom II, Athlon, Athlon X2, Athlon II and Older Intel Xeon and Intel
Core Architecture and Pentium CPUs.  
* We also do not support AMD Carrizo and Kaveri APU as host for compliant dGPU
 attachments.
* Thunderbolt 1 and 2 enabled GPU's are not supported by ROCm. Thunderbolt 1 & 2
are PCIe Gen2 based.
* AMD Carrizo based APUs have limited support due to OEM & ODM's choices when it
comes to some key configuration parameters. On point, we have observed that
Carrizo Laptops, AIOs and Desktop systems showed inconsistencies in exposing and
enabling the System BIOS parameters required by the ROCm stack. Before
purchasing a Carrizo system for ROCm, please verify that the BIOS provides an
option for enabling IOMMUv2. If this is the case, the final requirement is
associated with correct CRAT table support - please inquire with the OEM about 
the latter.
* AMD Merlin/Falcon Embedded System is also not currently supported by the public Repo. 

#### Support for future APUs
We are well aware of the excitement and anticipation built around using ROCm
with an APU system which fully exposes Shared Virtual Memory alongside and cache
coherency between the CPU and GPU. To this end, in 2017 we plan on testing 
commercial AM4 motherboards for the Bristol Ridge and Raven Ridge families of 
APUs. Just like you, we still waiting for access to them! Once we have the first
boards in the lab we will detail our experiences via our blog, as well as build
a list of motherboard that are qualified for use with ROCm.

### New Features to ROCm 

#### Developer preview of the new OpenCl 1.2 compatible language runtime and compiler

 * OpenCL 2.0 compatible kernel language support with OpenCL 1.2 compatible
   runtime 
 * Supports offline ahead of time compilation today;
   during the Beta phase we will add in-process/in-memory compilation. 
 * Binary Package support for Ubuntu 14.04 and 16.04 
 
#### IPC support 

### The Latest ROCm Platform - ROCm 1.4
The latest tested version of the drivers, tools, libraries and source code for
the ROCm platform have been released and are available under the roc-1.4.0 tag
of the following GitHub repositories:

* [ROCK-Kernel-Driver](https://github.com/RadeonOpenCompute/ROCK-Kernel-Driver/tree/roc-1.4.0)
* [ROCR-Runtime](https://github.com/RadeonOpenCompute/ROCR-Runtime/tree/roc-1.4.0)
* [ROCT-Thunk-Interface](https://github.com/RadeonOpenCompute/ROCT-Thunk-Interface/tree/roc-1.4.0)
* [HCC compiler](https://github.com/RadeonOpenCompute/hcc/tree/roc-1.4.x)
* [LLVM-AMDGPU-Assembler-Extra](https://github.com/RadeonOpenCompute/LLVM-AMDGPU-Assembler-Extra/tree/roc-1.4.x)
* [ROC-smi](https://github.com/RadeonOpenCompute/ROC-smi/tree/roc-1.4.x)
* [HIP](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP)
* [HIP-Examples](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP-Examples)

Additionally, the following mirror repositories that support the HCC compiler
are also available on GitHub, and frozen for the roc-1.4.0 release:

* [llvm](https://github.com/RadeonOpenCompute/llvm/tree/roc-1.4.x)
* [clang](https://github.com/RadeonOpenCompute/clang/tree/roc-1.4.x)

#### Supported Operating Systems

The ROCm platform has been tested on the following operating systems:
 * Ubuntu 14.04.04
 * Ubuntu 16.04
 * Fedora 23

### Installing from AMD ROCm Repositories
AMD is hosting both debian and rpm repositories for the ROCm 1.4 packages. The
packages in both repositories have been signed to ensure package integrity.
Directions for each repository are given below:

#### Debian repository - apt-get

##### Add the ROCm apt repository
For Debian based systems, like Ubuntu, configure the Debian ROCm repository as
follows:

```shell
wget -qO - http://packages.amd.com/rocm/apt/debian/rocm.gpg.key | sudo apt-key add -
sudo sh -c 'echo deb [arch=amd64] http://packages.amd.com/rocm/apt/debian/ xenial main > /etc/apt/sources.list.d/rocm.list'
```
The gpg key might change, so it may need to be updated when installing a new 
release.

##### Install or Update
Next, update the apt-get repository list and install/update the rocm package:

>**Warning**: Before proceeding, make sure to completely
>[uninstall any pre-release ROCm packages](https://github.com/RadeonOpenCompute/ROCm#removing-pre-release-packages):

```shell
sudo apt-get update
sudo apt-get install rocm
```
Then, make the ROCm kernel your default kernel. If using grub2 as your
bootloader, you can edit the `GRUB_DEFAULT` variable in the following file:

```shell
sudo vi /etc/default/grub
sudo update-grub
```

Once complete, reboot your system.

We recommend you [verify your installation](https://github.com/RadeonOpenCompute/ROCm#verify-installation) to make sure everything completed successfully.

#### To intall ROCm with Developer Preview of OpenCL 

#####Start by following the istruction of installing ROCm with Debian Repository:

 at the step "sudo apt-get install rocm" replace it with 
 
 sudo apt-get install rocm opencl-rocm
 
 Then follow the direction for Debian Repository 
 
###### Upon restart, To test your OpenCL instance 

 Build and run Hello World OCL app..

HelloWorld sample:
 wget https://raw.githubusercontent.com/bgaster/opencl-book-samples/master/src/Chapter_2/HelloWorld/HelloWorld.cpp
 wget https://raw.githubusercontent.com/bgaster/opencl-book-samples/master/src/Chapter_2/HelloWorld/HelloWorld.cl

 Build it using the default ROCm OpenCL include and library locations:
 g++ -I /opt/rocm/opencl/include/opencl1.2 ./HelloWorld.cpp -o HelloWorld -L /opt/rocm/opencl/lib/x86_64 -lOpenCL

 Run it:
 ./HelloWorld


##### Un-install
To un-install the entire rocm-dev development package execute:

```shell
sudo apt-get autoremove rocm
```

##### Installing development packages for cross compilation
It is often useful to develop and test on different systems. In this scenario,
you may prefer to avoid installing the ROCm Kernel to your development system.

In this case, install the development subset of packages:

```shell
sudo apt-get update
sudo apt-get install rocm-dev
```

>**Note:** To execute ROCm enabled apps you will require a system with the full
>ROCm driver stack installed

##### Removing pre-release packages
If you installed any of the ROCm pre-release packages from github, they will
need to be manually un-installed:

```shell
sudo apt-get purge libhsakmt
sudo apt-get purge radeon-firmware
sudo apt-get purge $(dpkg -l | grep 'kfd\|rocm' | grep linux | grep -v libc | awk '{print $2}')
```

If possible, we would recommend starting with a fresh OS install.

#### RPM repository - dnf (yum)

A dnf (yum) repository is also available for installation of rpm packages.
To configure a system to use the ROCm rpm directory create the file
/etc/yum.repos.d/rocm.repo with the following contents:

```shell
[remote]

name=ROCm Repo

baseurl=http://packages.amd.com/rocm/yum/rpm/

enabled=1

gpgcheck=0
```
Execute the following commands:

```shell
sudo dnf clean all
sudo dnf install rocm
```

As with the debian packages, it is possible to install rocm-dev or rocm-kernel
individually. To uninstall the packages execute:

```shell
sudo dnf remove rocm
```
#### Manual installation steps for Fedora 23

A fully functional Fedora installation requires a few manual steps to properly 
setup, including:
 * [Building compatible libc++ and libc++abi libraries for Fedora](https://github.com/RadeonOpenCompute/hcc/wiki#fedora)

#### Verify Installation

To verify that the ROCm stack completed successfully you can execute to HSA
vectory\_copy sample application (we do recommend that you copy it to a
separate folder and invoke make therein):

```shell
cd /opt/rocm/hsa/sample
make
./vector_copy
```

#### Closed Source Components
The ROCm platform relies on a few closed source components to provide legacy
functionality like HSAIL finalization and debugging/profiling support. These
components are only available through the ROCm repositories, and will either be
deprecated or become open source components in the future. These components are
made available in the following packages:

*  hsa-ext-rocr-dev
*  OpenCL Developer Preview for version 1.4 is closed source (applies only to 
   this release). 

### Getting ROCm Source Code
Modifications can be made to the ROCm 1.4 components by modifying the open
source code base and rebuilding the components. Source code can be cloned from
each of the GitHub repositories using git, or users can use the repo command
and the ROCm 1.4 manifest file to download the entire ROCm 1.4 source code.

#### Installing repo
Google's repo tool allows you to manage multiple git repositories
simultaneously. You can install it by executing the following commands:

```shell
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```
Note: make sure ~/bin exists and it is part of your PATH

#### Cloning the code
```shell
mkdir ROCm && cd ROCm
repo init -u https://github.com/RadeonOpenCompute/ROCm.git -b roc-1.4.0
repo sync
```

These series of commands will pull all of the open source code associated with
the ROCm 1.4 release.

* OpenCL Runtime and Compiler will be submitted to the Khronos Groupm, prior to
  the final release, for conformance testing.
