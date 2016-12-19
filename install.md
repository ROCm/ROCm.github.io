---
layout: default
title: ROCm Install
---

## ROCm Installation Guide

### Release Notes

ROCm release notes are available [here](https://github.com/RadeonOpenCompute/ROCm/blob/master/README.md).  

## Are You Ready to ROCK?
The ROCm Platform bringing a rich foundation to advanced computing by better intergrating the CPU and GPU to solve realworld problems.

On April 25th, 2016, we delivered ROCm 1.0 built around three core foundation elements:

Open Hetrogenous Computing Platform (Linux(R) Driver and Runtime Stack) optimized for HPC & Ultra-scale class computing
Heterogeneous C and C++ Single Source to better address the whole system computation not just a gpu device
HIP acknowledging the need for platform choice when utilizing GPU computing API

Using our knowledge of the HSA Standards and, more importantly, the HSA
Runtime we have been able to successfully extended support to the dGPU with
critical features for NUMA class acceleration. As a result, the ROCK driver is
composed of several components based on our efforts to develop the
Heterogeneous System Architecture for APUs, including the new AMDGPU driver,
the Kernel Fusion Driver (KFD), the HSA+ Runtime and an LLVM based compilation
stack for the building of key language support. This support starts with AMD’s
FIJI Family of dGPU, and has expanded to include the Hawaii dGPU Family in ROCm 1.2
ROCm 1.3 expands this support to include the Polaris Family of ASICS.

#### Supported CPU's 
ROCm Platform Leverage PCIe Atomics which are only supported on PCIe Gen3 Enabled CPU's and PCIe Switches like Broadcomm PLX. When you install your GPU's Make sure you install them on real PCIe Gen3 x16 or x8 lanes directly on CPU's Root I/O controler or PCIe Switch directly attacted to the CPU's Root I/O contorler.  We seen many issue with Consumer motherboard support Physical x16 Conecectors, but the elecitical only conected at PCIe Gen x4 off the southbridge PCIe I/O controler.  

  * Intel Xeon E5 v3 or newer CPU's 
  * Intel Xeon E3 v3 or newer CPU's 
  * Intel Core i7 v3, Core i5 v3, Core i3 v3 or newer CPU's  
  * AMD Ryzen CPU's
  * AMD Naples Server CPU 
  * Cavium Thunder X Server Processor 

* Our GF7 GPU's Radeon R9 290, R9 390, AMD FirePro S9150, S9170 do not support PCIe Atomics. For these GPU's we still recommend PCIe Gen3 enabled CPU's. 


#### Not Supported or Very Limited Support Under ROCm 
* We do not support ROCm with PCIe Gen 2 enabled CPU's such as the AMD Opteron, Phenom, Phenom II, , Athlon, Athlon X2, Athlon II and Older Intel Xeon and Intel Core Architecture and Pentium CPU's.  
* We also do not support AMD Carizo and Kaveri APU with external GPU Attached are not supported by ROCm 

* AMD Carizo based APU have limited support due to OEM & ODM's Carizo enabled Laptop, All In One System and Desktop system had inconsistency in supporting the correct System BIOS configurations for ROCm driver enablement. Before you buy a Carizo system to run ROCm.  You should check the SBIOS to see if has an option to enable IOMMUv2. If this is enabled, next we need test for the correct CRAT Table support to properly configure the driver.   

#### Potential Future APU Support
I know many of you are looking forward to support ROCm on APU system which support Fine Grained Shared Virtual Memory and cache coherency between the CPU and GPU. In the 2017 we plan on testing commercial AM4 Socketed Bristol Ridge and Raven Ridge motherboard. Just like we still waiting to get access to them, once we get our first board we blog about the experience and begin building up a list of motherboard that are qualified with ROCm

### New Features to ROCm 

#### Developer preview of the new OpenCl 1.2 compatible language runtime and compiler

 * OpenCL 2.0 compatible kernel language support with OpenCL 1.2 compatible runtime 
 * Supports offline ahead of time compilation today, for Beta we will be adding in-process/in-memory compilation. 
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

In addition the following mirror repositories that support the HCC compiler are
also available on GitHub, and frozen for the roc-1.4.0 release:

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
The gpg key might change, so it may need to be updated when installing a new release.

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

A dnf (yum) repostiory is also available for installation of rpm packages. To configure a
system to use the ROCm rpm directory create the file /etc/yum.repos.d/rocm.repo with
the following contents:

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

As with the debian packages, it is possible to install rocm-dev or rocm-kernel individually.
To uninstall the packages execute:

```shell
sudo dnf remove rocm
```
#### Manual installation steps for Fedora 23

A fully functional Fedora installation requires a few manual steps to properly setup, including:
 * [Building compatible libc++ and libc++abi libraries for Fedora](https://github.com/RadeonOpenCompute/hcc/wiki#fedora)

#### Verify Installation

To verify that the ROCm stack completed successfully you can execute to HSA
vectory\_copy sample application:

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
*  OpenCL Developer Preview for version 1.4 is closed source for this release only. 

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

* OpenCL Runtime and Compiler will be submited to Khronos Group for conformance prior final release. 
