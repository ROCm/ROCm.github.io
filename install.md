---
layout: default
title: ROCm Install
---

# Are You Ready to ROCK?!

## ROCm Installation Guide

The ROCm platform brings a rich foundation to advanced computing by
better intergrating the CPU and GPU to solve real-world problems. On
April 25, 2016, we delivered ROCm 1.0, building on three foundational
elements:

 * Open heterogeneous-computing platform (Linux driver and run-time stack) optimized for HPC and ultrascale computing
 * Single heterogeneous C and C++ source to  better address the whole system, not just a GPU
 * Use of HIP to acknowledge the need for platform choice when employing a GPU-compute API

Using our knowledge of the Heterogeneous System Architecture (HSA)
standards and, more importantly, the HSA Runtime, we successfully
extended support to the dGPU with features critical for NUMA-class
acceleration. As a result, the ROCK driver comprises a number of
components originating  from our efforts to develop HSA for APUs,
including the new AMD GPU driver, the Kernel Fusion Driver (KFD), the
HSA+ Runtime and an LLVM-based compilation stack to support major
languages. This support begins with AMD’s Radeon R9 Fury, Radeon R9
Nano, Radeon R9 Fury X and FirePro S9300x2 dGPUs, but it’s slated to
include future ASICS.

### The Latest Platform: ROCm 1.1

The latest tested version of the drivers, tools, libraries and source
code for the ROCm platform are available now under the roc-1.1.0 tag
of the following GitHub repositories:

 * ROCK-Kernel-Driver
 * ROCR-Runtime
 * ROCT-Thunk-Interface
 * HCC compiler
 * LLVM-AMDGPU-Assembler-Extra
 * ROC-smi
 * ROCnRDMA
 * HIP
 * HIP-Examples

Also, the following mirror repositories that support the HCC compiler
are available on GitHub and are frozen for the roc-1.1.0 release:

 * llvm
 * clang

[Click here to access the most current readme for the ROCm repository
installation.](https://github.com/RadeonOpenCompute/ROCm/blob/master/README.md)

#### Installing From AMD ROCm Repositories

AMD is hosting both Debian and RPM repositories for the ROCm 1.1
packages. The packages in both repositories are signed to ensure their
integrity. Below are directions for each repository.

###### Supported Operating Systems

The ROCm platform has undergone testing on the following operating
systems:

 * Ubuntu 14.04.04
 * Fedora 23

Experimental support is available for these operating systems:

 * Ubuntu 16.04
 * Fedora 22

###### Debian Repository: apt-get

For Debian-based systems, such as Ubuntu, configure the Debian ROCm
repository as follows:

```bash
wget -qO - http://packages.amd.com/rocm/apt/debian/rocm.gpg.key | sudo apt-key add -
sudo sh -c 'echo deb [arch=amd64] http://packages.amd.com/rocm/apt/debian/ trusty main > /etc/apt/sources.list.d/rocm.list'
```

###### Install or Update

Next, update the apt-get repository list and install/update the
ROCm package.

Warning: before proceeding, make sure you completely uninstall any
prerelease ROCm packages by executing the command

```
sudo apt-get update
sudo apt-get install rocm
```

Next, make the ROCm kernel your default kernel. If you’re using Grub2
as your bootloader, you can edit the GRUB_DEFAULT variable:
```
sudo vi /etc/default/grub
sudo update-grub
```

Once complete, reboot your system.

We recommend that you [verify](#verify-installation)  your
installation to ensure everything completed successfully.

###### Ubuntu Uninstall

To uninstall the entire rocm-dev development package, execute:
```
sudo apt-get autoremove rocm
```

###### Installing Development Packages for Cross-Compilation

Developing and testing software on different systems is often useful.
In this scenario, you may prefer to avoid installing the ROCm kernel
on your development system. If so, install the development subset of
packages:

```
sudo apt-get update
sudo apt-get install rocm-dev
```

Note: to execute ROCm-enabled apps, you’ll need a system with the full
ROCm driver stack installed.

###### RPM Repository: dnf (yum)

A dnf (yum) repository is also available for installation of RPM
packages. To configure a system to use the ROCm RPM directory, create
the file <code>/etc/yum.repos.d/rocm.repo</code> with the following
contents:

```
[remote]
name=ROCm Repo
baseurl=http://packages.amd.com/rocm/yum/rpm/
enabled=1
gpgcheck=0
```

Execute this command:

```
sudo dnf clean all
sudo dnf install rocm
```

As with the Debian packages, you can install rocm-dev or rocm-kernel
individually. To uninstall them, execute:

```
sudo dnf remove rocm
```

###### Verify Installation

To verify that the ROCm stack installation was successful, execute to
HSA the vectory_copy sample application:

```
cd /opt/rocm/hsa/sample
make
./vector_copy</code>.
```

###### Closed-Source Components

The ROCm platform relies on a few closed-source components to provide
legacy functions such as HSAIL completion and debugging/profiling
support. These components are only available through the ROCm
repositories and will eventually either be deprecated or become open
source. They are available in the hsa-ext-rocr-dev packages.

###### Getting ROCm Source Code

You can modify the ROCm 1.1 components by changing the open-source
code base and rebuilding them. You can clone source code from each of
the GitHub repositories using git, or use the repo command and the
ROCm 1.1 manifest file to download the entire ROCm 1.1 source code.

###### Installing Repo

Google's repo tool allows you to manage multiple git repositories
simultaneously. Install it by executing:

```
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

Note: make sure `~/bin` exists and is part of your path.

###### Cloning the Code

Execute the following commands to clone the code:

```
mkdir ROCm && cd ROCm
repo init -u https://github.com/RadeonOpenCompute/ROCm.git
repo sync
```
