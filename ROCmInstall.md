---
layout: default
title: ROCm Install
---

## Are You Ready to ROCK?
The ROCm Platform brings a rich foundation to advanced computing by seamlessly
 integrating the CPU and GPU with the goal of solving real-world problems.

#### Supported CPUs

Starting with ROCm 1.8, we have relaxed the requirements for PCIe Atomics on Vega 10 (GFX9) GPUs, and we have similarly opened up more options for number of PCIe lanes. With this release, these GFX9 GPUs can support CPUs without PCIe Atomics and, for example, run on PCIe  Gen2 x1 lanes. To enable this option, please set the environment variable `HSA_ENABLE_SDMA=0`.

Currently, our GFX8 GPUs (Fiji & Polaris family) still need to use PCIe Gen 3 and PCIe Atomics, but are looking at relaxing this in a future release, once we have fully tested firmware.

Current CPUs which support PCIe Gen3 + PCIe Atomics are: 
  * AMD Ryzen CPUs;
  * AMD EPYC CPUs;  
  * Intel Xeon E7 V3  or newer CPUs;
  * Intel Xeon E5 v3 or newer CPUs; 
  * Intel Xeon E3 v3 or newer CPUs;
  * Intel Core i7 v4, Core i5 v4, Core i3 v4 or newer CPUs (i.e. Haswell family or newer).

For Fiji and Polaris GPUs, the ROCm platform leverages PCIe Atomics (Fetch and Add, Compare and Swap, 
Unconditional Swap, AtomicsOp Completion).
PCIe Atomics are only supported on PCIe Gen3 enabled CPUs and PCIe Gen3 switches like
Broadcom PLX. When you install your GPUs, make sure you install them in a fully
PCIe Gen3 x16 or x8, x4 or x1  slot attached either directly to the CPU's Root I/O 
controller or via a PCIe switch directly attached to the CPU's Root I/O 
controller. In our experience, many issues stem from trying to use consumer 
motherboards which provide physical x16 connectors that are electrically 
connected as e.g. PCIe Gen2 x4, PCIe slots connected via the 
Southbridge PCIe I/O controller, or PCIe slots connected through a PCIe switch that does
not support PCIe atomics. 
 
Experimental support for our Hawaii (GFX7) GPUs (Radeon R9 290, R9 390, FirePro W9100, S9150, S9170)
does not require or take advantage of PCIe Atomics. However, we still recommend that you use a CPU
from the list provided above for compatibility purposes.

#### Not supported or very limited support under ROCm 
###### Limited support 

* ROCm 1.8 and Vega10 should support PCIe Gen2 enabled CPUs such as the AMD Opteron, Phenom, Phenom II, Athlon, Athlon X2, Athlon II and older Intel Xeon and Intel Core Architecture and Pentium CPUs. However, we have done very limited testing on these configurations, since our test farm has been catering to CPU listed above. This is where we need community support; if you find problems on such setups, please report these issues.
 * Thunderbolt 1, 2, and 3 enabled breakout boxes should now be able to work with ROCm. Thunderbolt 1 and 2 are PCIe Gen2 based, and thus are only supported with GPUs that do not require PCIe Gen 3 atomics (i.e. Vega 10). However, we have done no testing on this configuration and would need comunity support due to limited access to this type of equipment 

###### Not supported 

* We do not support GFX8-class GPUs (Fiji, Polaris, etc.) on CPUs that do not have PCIe Gen 3 with PCIe atomics.
  * As such, do not support AMD Carrizo and Kaveri APUs as hosts for such GPUs..
  * Thunderbolt 1 and 2 enabled GPUs are not supported by GFX8 GPUs on ROCm. Thunderbolt 1 & 2 are PCIe Gen2 based.
* AMD Carrizo based APUs have limited support due to OEM & ODM's choices when it comes to some key configuration parameters. In particular, we have observed that Carrizo laptops, AIOs, and desktop systems showed inconsistencies in exposing and enabling the System BIOS parameters required by the ROCm stack. Before purchasing a Carrizo system for ROCm, please verify that the BIOS provides an option for enabling IOMMUv2 and that the system BIOS properly exposes the correct CRAT table - please inquire with the OEM about the latter.
 * AMD Merlin/Falcon Embedded System is not currently supported by the public repo.
 * AMD Raven Ridge APU are currently not supported

### New features to ROCm 1.8.3

* ROCm 1.8.3 is a minor update meant to fix compatibility issues on Ubuntu releases running kernel 4.15.0-33

### New features as of ROCm 1.8.2

#### DKMS driver installation

 * Debian packages are provided for DKMS on Ubuntu
 * RPM packages are provided for CentOS/RHEL 7.4 and 7.5 support
 * See the [ROCT-Thunk-Interface](https://github.com/RadeonOpenCompute/ROCT-Thunk-Interface/tree/roc-1.8.x) and [ROCK-Kernel-Driver](https://github.com/RadeonOpenCompute/ROCK-Kernel-Driver/tree/roc-1.8.x) for additional documentation on driver setup

#### New distribution support 

 * Binary package support for Ubuntu 16.04
 * Binary package support for CentOS 7.4 and 7.5
 * Binary package support for RHEL 7.4 and 7.5
 
#### Improved OpenMPI via UCX support 

 * UCX support for OpenMPI
 * ROCm RDMA

### The latest ROCm platform - ROCm 1.8.3

The latest tested version of the drivers, tools, libraries and source code for
the ROCm platform have been released and are available under the roc-1.8.x or rocm-1.8.x tag
of the following GitHub repositories:

* [ROCK-Kernel-Driver](https://github.com/RadeonOpenCompute/ROCK-Kernel-Driver/tree/roc-1.8.x)
* [ROCR-Runtime](https://github.com/RadeonOpenCompute/ROCR-Runtime/tree/roc-1.8.x)
* [ROCT-Thunk-Interface](https://github.com/RadeonOpenCompute/ROCT-Thunk-Interface/tree/roc-1.8.x)
* [ROC-smi](https://github.com/RadeonOpenCompute/ROC-smi/tree/roc-1.8.x)
* [HCC compiler](https://github.com/RadeonOpenCompute/hcc/tree/roc-1.8.x)
* [compiler-runtime](https://github.com/RadeonOpenCompute/compiler-rt/tree/roc-1.8.x)
* [HIP](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP/tree/roc-1.8.x)
* [HIP-Examples](https://github.com/GPUOpen-ProfessionalCompute-Tools/HIP-Examples/tree/roc-1.8.x)
* [atmi](https://github.com/RadeonOpenCompute/atmi/tree/0.3.7)

Additionally, the following mirror repositories that support the HCC compiler
are also available on GitHub, and frozen for the rocm-1.8.3 release:

* [llvm](https://github.com/RadeonOpenCompute/llvm/tree/roc-1.8.x)
* [ldd](https://github.com/RadeonOpenCompute/lld/tree/roc-1.8.x)
* [hcc-clang-upgrade](https://github.com/RadeonOpenCompute/hcc-clang-upgrade/tree/roc-1.8.x)
* [ROCm-Device-Libs](https://github.com/RadeonOpenCompute/ROCm-Device-Libs/tree/roc-1.8.x)

#### Supported Operating Systems - New operating systems available

The ROCm 1.8.3 platform has been tested on the following operating systems:
 * Ubuntu 16.04
 * CentOS 7.4 &. 7.5 (Using devetoolset-7 runtime support)
 * RHEL 7.4. &. 7.5  (Using devetoolset-7 runtime support)

### Installing from AMD ROCm repositories

AMD is hosting both Debian and RPM repositories for the ROCm 1.8.3 packages at this time.

The packages in the Debian repository have been signed to ensure package integrity.

#### Installing from a Debian repository

##### First make sure your system is up to date 

```shell
sudo apt update
sudo apt dist-upgrade
sudo apt install libnuma-dev
sudo reboot
```

##### Add the ROCm apt repository

For Debian based systems, like Ubuntu, configure the Debian ROCm repository as
follows:

```shell
wget -qO - http://repo.radeon.com/rocm/apt/debian/rocm.gpg.key | sudo apt-key add -
echo 'deb [arch=amd64] http://repo.radeon.com/rocm/apt/debian/ xenial main' | sudo tee /etc/apt/sources.list.d/rocm.list
```
The gpg key might change, so it may need to be updated when installing a new release. 
If the key signature verification is failed while update, please re-add the key from 
ROCm apt repository. The current rocm.gpg.key is not avialable in a standard key ring 
distribution, but has the following sha1sum hash:

f7f8147431c75e505c58a6f3a3548510869357a6  rocm.gpg.key

##### Install

Next, update the apt repository list and install the rocm package:

>**Warning**: Before proceeding, make sure to completely
>[uninstall any previous ROCm package](https://github.com/RadeonOpenCompute/ROCm#removing-pre-release-packages):

```shell
sudo apt update
sudo apt install rocm-dkms
```

###### Next set your permissions 

With move to upstreaming the KFD driver and the support of DKMS,  for all Console aka headless user, you will need to add all  your users to the  'video" group by setting the Unix permissions

Configure 
Ensure that your user account is a member of the "video" group prior to using the ROCm driver. You can find which groups you are a member of with the following command:

```shell
groups
```

To add yourself to the video group you will need the sudo password and can use the following command:

```shell
sudo usermod -a -G video $LOGNAME 
``` 

You may want to ensure that any future users you add to your system are put into the "video" group by default. To do that, you can run the following commands:
```shell
echo 'ADD_EXTRA_GROUPS=1' | sudo tee -a /etc/adduser.conf
echo 'EXTRA_GROUPS=video' | sudo tee -a /etc/adduser.conf
```

Once complete, reboot your system.

Upon Reboot run the following commands to verify that the ROCm installation waas successful. If you see your GPUs listed by both of these commands, you should be ready to go!
```shell
/opt/rocm/bin/rocminfo 
/opt/rocm/opencl/bin/x86_64/clinfo 
``` 

Note that, to make running ROCm programs easier, you may wish to put the ROCm libraries in your LD_LIBRARY_PATH environment variable and the ROCm binaries in your PATH.
```shell
echo 'export LD_LIBRARY_PATH=/opt/rocm/opencl/lib/x86_64:/opt/rocm/hsa/lib:$LD_LIBRARY_PATH' | sudo tee -a /etc/profile.d/rocm.sh
echo 'export PATH=$PATH:/opt/rocm/bin:/opt/rocm/profiler/bin:/opt/rocm/opencl/bin/x86_64' | sudo tee -a /etc/profile.d/rocm.sh
```

If you have an [Install Issue](https://rocm.github.io/install_issues.html) please read this FAQ .

###### Vega10 users who want to run ROCm on a system that does not support PCIe atomics must set HSA_ENABLE_SDMA=0

Currently, if you want to run ROCm on a Vega10 GPU (GFX9) on a system without PCIe atomics, you must turn off SDMA functionality.

```shell
export HSA_ENABLE_SDMA=0
```

###### Performing an OpenCL-only Installation of ROCm

Some users may want to install a subset of the full ROCm installation. In particular, if you are trying to install on a system with a limited amount of storage space, or which will only run a small collection of known applications, you may want to install only the packages that are required to run OpenCL applications. To do that, you can run the following installation command **instead** of the command to install `rocm-dkms`.

```shell
sudo apt-get install dkms rock-dkms rocm-opencl
```

###### Upon restart, to test your OpenCL instance 

Build and run Hello World OCL app.

HelloWorld sample:

```shell
 wget https://raw.githubusercontent.com/bgaster/opencl-book-samples/master/src/Chapter_2/HelloWorld/HelloWorld.cpp
 wget https://raw.githubusercontent.com/bgaster/opencl-book-samples/master/src/Chapter_2/HelloWorld/HelloWorld.cl
```

 Build it using the default ROCm OpenCL include and library locations:

```shell
g++ -I /opt/rocm/opencl/include/ ./HelloWorld.cpp -o HelloWorld -L/opt/rocm/opencl/lib/x86_64 -lOpenCL
```

 Run it:

 ```shell
 ./HelloWorld
```

##### How to un-install from Ubuntu 16.04

To un-install the entire rocm development package execute:

```shell
sudo apt autoremove rocm-dkms
```

##### Installing development packages for cross compilation

It is often useful to develop and test on different systems. In this scenario,
you may prefer to avoid installing the ROCm Kernel to your development system.

In this case, install the development subset of packages:

```shell
sudo apt update
sudo apt install rocm-dev
```

>**Note:** To execute ROCm enabled apps you will require a system with the full
>ROCm driver stack installed

##### Removing pre-release packages

If you installed any of the ROCm pre-release packages from github, they will
need to be manually un-installed:

```shell
sudo apt purge hsakmt-roct
sudo apt purge hsakmt-roct-dev
sudo apt purge compute-firmware
sudo apt purge $(dpkg -l | grep 'kfd\|rocm' | grep linux | grep -v libc | awk '{print $2}')
```

If possible, we would recommend starting with a fresh OS install.

### CentOS/RHEL 7 (both 7.4 and 7.5) Support

Support for CentOS/RHEL 7 has been added in ROCm 1.8, but requires a special 
runtime environment provided by the RHEL Software Collections and additional
dkms support packages to properly install in run.

#### Preparing RHEL 7 for installation

RHEL is a subscription based operating system, and must enable several external
repositories to enable installation of the devtoolset-7 environment and the DKMS
support files. These steps are not required for CentOS.

First, the subscription for RHEL must be enabled and attached to a pool id. Please
see Obtaining an RHEL image and license page for instructions on registering your
system with the RHEL subscription server and attaching to a pool id.


Second, enable the following repositories:

```shell
sudo subscription-manager repos --enable rhel-server-rhscl-7-rpms
sudo subscription-manager repos --enable rhel-7-server-optional-rpms
sudo subscription-manager repos --enable rhel-7-server-extras-rpms
```

Third, enable additional repositories by downloading and installing the epel-release-latest-7 repository RPM:

```shell
sudo rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

#### Install and setup Devtoolset-7

To setup the Devtoolset-7 environment, follow the instructions on this page:

https://www.softwarecollections.org/en/scls/rhscl/devtoolset-7/

Note that devtoolset-7 is a Software Collections package, and is not supported by AMD.

#### Prepare CentOS/RHEL 7.4 or 7.5 for DKMS Install

Installing kernel drivers on CentOS/RHEL 7.4/7.5 requires dkms tool being installed:

```shell
sudo yum install -y epel-release
sudo yum install -y dkms kernel-headers-`uname -r`
```


At this point they system can install ROCm using the DKMS drivers.

Installing ROCm on the system
At this point ROCm can be installed on the target system. Create a /etc/yum.repos.d/rocm.repo file with the following contents:

```shell
[ROCm]
name=ROCm
baseurl=http://repo.radeon.com/rocm/yum/rpm
enabled=1
gpgcheck=0
```

The repo's URL should point to the location of the repositories repodata database. Install ROCm components using these commands:

```shell
sudo yum install rocm-dkms
```

The rock-dkms component should be installed and the /dev/kfd device should be available on reboot.

Ensure that your user account is a member of the "video" or "wheel" group prior to using the ROCm driver.
You can find which groups you are a member of with the following command:

```shell
groups
```

To add yourself to the video (or wheel) group you will need the sudo password and can use the
following command:

```shell
sudo usermod -a -G video $LOGNAME 
```

Current release supports up to CentOS/RHEL 7.4 and 7.5. Users should update to the latest version of the OS:

```shell
sudo yum update
```
###### Vega10 users who want to run ROCm on a system that does not support PCIe atomics must set HSA_ENABLE_SDMA=0

Currently, if you want to run ROCm on a Vega10 GPU (GFX9) on a system without PCIe atomics, you must turn off SDMA functionality.

```shell
export HSA_ENABLE_SDMA=0
```

###### Performing an OpenCL-only Installation of ROCm

Some users may want to install a subset of the full ROCm installation. In particular, if you are trying to install on a system with a limited amount of storage space, or which will only run a small collection of known applications, you may want to install only the packages that are required to run OpenCL applications. To do that, you can run the following installation command **instead** of the command to install `rocm-dkms`.

```shell
sudo yum install rock-dkms rocm-opencl
```

#### Compiling applications using hcc, hip, etc.

To compile applications or samples, please use gcc-7.2 provided by the devtoolset-7 environment.
To do this, compile all applications after running this command: 

```shell
scl enable devtoolset-7 bash
```
#### How to un-install ROCm from CentOS/RHEL 7.4

To un-install the entire rocm development package execute:

```shell
sudo yum autoremove rocm-dkms
```

#### Known Issues / Workarounds

##### If you Plan to Run with X11 - we are seeing X freezes under load

In ROCm 1.8.3, the kernel parameter 'noretry' has been set to 1 to improve overall system performance. However it has been proven to bring instability to graphics driver shipped with Ubuntu. This is an ongoing issue and we are looking into it.

Before that, please try apply this change by changing noretry bit to 0.

```shell
echo 0 | sudo tee /sys/module/amdkfd/parameters/noretry
```

Files under /sys won't be preserved after reboot so you'll need to do it every time.

One way to keep noretry=0 is to change /etc/modprobe.d/amdkfd.conf and make it be:

options amdkfd noretry=0

Once it's done, run sudo update-initramfs -u. Reboot and verify /sys/module/amdkfd/parameters/noretry stays as 0.

##### If you are you are using hipCaffe Alexnet training on ImageNet - we are seeing sporadic hangs of hipCaffe during training

###### Vega10 users who want to run ROCm on a system that does not support PCIe atomics must set HSA_ENABLE_SDMA=0

Currently, if you want to run ROCm on a Vega10 GPU (GFX9) on a system without PCIe atomics, you must turn off SDMA functionality.

```shell
export HSA_ENABLE_SDMA=0
```

#### Closed source components

The ROCm platform relies on a few closed source components to provide legacy
functionality like HSAIL finalization and debugging/profiling support. These
components are only available through the ROCm repositories, and will either be
deprecated or become open source components in the future. These components are
made available in the following packages:

*  hsa-ext-rocr-dev

### Getting ROCm source code

Modifications can be made to the ROCm 1.8 components by modifying the open
source code base and rebuilding the components. Source code can be cloned from
each of the GitHub repositories using git, or users can use the repo command
and the ROCm 1.8 manifest file to download the entire ROCm 1.8 source code.

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
repo init -u https://github.com/RadeonOpenCompute/ROCm.git -b roc-1.8.3
repo sync
```
These series of commands will pull all of the open source code associated with
the ROCm 1.8 release. Please ensure that ssh-keys are configured for the
target machine on GitHub for your GitHub ID.

* OpenCL Runtime and Compiler will be submitted to the Khronos Group, prior to
  the final release, for conformance testing.
