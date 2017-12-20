---
layout: default
title: ROCm Install
---

## ROCm GPU Server Driver Installation Guide for Linux 

### Introduction 
The ROCm Platform brings a rich foundation to advanced computing by seamlessly integrating the CPU and GPU with the goal of solving real-world problems.

ROCm started  with just the support of AMD’s FIJI Family of dGPUs. Starting with ROCm 1.3 we further extends support to include the Polaris Family of ASICs. With ROCm 1.6 we added Vega Family of products. 

#### New too ROCm 1.7 is the DKMS driver installation

 * New driver installation uses Dynamic Kernel Module Support (DKMS)
 * Only amdkfd and amdgpu kernel modules are installed to support AMD hardware
 * Currently only Debian packages are provided for DKMS (no Fedora suport available)
 * See the [ROCT-Thunk-Interface](https://github.com/RadeonOpenCompute/ROCT-Thunk-Interface/tree/roc-1.7.x) and [ROCK-Kernel-Driver](https://github.com/RadeonOpenCompute/ROCK-Kernel-Driver/tree/roc-1.7.x) for additional documentation on driver setup

### System Requirements 

To use ROCm on your system you need the following: 
* ROCm Capable CPU and GPU 
	* PCIe Gen 3 Enabled CPU with PCIe Platform Atomics 
		* [More about how ROCm uses PCIe Atomics](https://rocm.github.io/ROCmPCIeFeatures.html)
	* ROCm enabled GPU's 
		* Radeon Instinct Family MI25, MI8, MI6 
		* Radeon Vega Frontier Edition 
		* [Broader Set of Tested Hardware](hardware.md)
* Supported Version of Linux with a specified GCC Compiler and ToolChain 


Table 1. Native Linux Distribution Support in ROCm  1.7

|Distribution	|Kernel	|GCC	|GLIBC	|
|:--------------|:------|:------|:------|
|x86_64		|	|	|       |		
|Ubuntu 16.04	|4.11	|5.40	|2.23   |		
	
### Pre Install Directions 

##### Verify You Have ROCm Capable GPU Installed int the System 

```shell
lspci | grep -i AMD
```
###### You will see list of AMD GPU's 

##### Verify You Have a Supported Version of Linux 

```shell
uname -m && cat /etc/*release
```

###### You will see some thing like for Ubuntu 

```shell
x86_64
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
```

##### Verify version of GCC 

```shell
gcc --version 
```

###### You will see 

```shell
gcc (Ubuntu 5.4.0-6ubuntu1~16.04.4) 5.4.0 20160609 
```

### Choose an Installation Method

Package manager Based Install 
A Package Manager Based Installation use your Linux Distro system's package management service.  
Ubuntu uses Debian  and Fedora RPM Packages

* Ubuntu 
* Fedora 

#### Ubuntu Install 

##### Add the Repo Server
For Debian based systems, like Ubuntu, configure the Debian ROCm repository as
follows:

```shell
wget -qO - http://repo.radeon.com/rocm/apt/debian/rocm.gpg.key | sudo apt-key add -
sudo sh -c 'echo deb [arch=amd64] http://repo.radeon.com/rocm/apt/debian/ xenial main > /etc/apt/sources.list.d/rocm.list'
```
The gpg key might change, so it may need to be updated when installing a new 
release. The current rocm.gpg.key is not avialable in a standard key ring distribution,
but has the following sha1sum hash:

f0d739836a9094004b0a39058d046349aacc1178  rocm.gpg.key

##### Install or update ROCm 
Next, update the apt-get repository list and install/update the rocm package:

>**Warning**: Before proceeding, make sure to completely
>[uninstall any previous ROCm package](https://github.com/RadeonOpenCompute/ROCm#removing-pre-release-packages):

```shell
sudo apt-get update
sudo apt-get install rocm-dkms rocm-opencl-dev
```

With move to upstreaming the KFD driver and the support of DKMS,  for all Console aka headless user you will need  add all  your users to the  'video" group by setting the unix permisions

```shell
sudo usermod -a -G video <username>
Once complete, reboot your system.
```

We recommend you [verify your installation](https://github.com/RadeonOpenCompute/ROCm#verify-installation) to make sure everything completed successfully.

------------------------------------


##### Post install verification 

###### Upon restart, To test your OpenCL instance 

Post Install all user need to part of the member of “video” group so set your Unix permisions for this. 

 Build and run Hello World OCL app..

HelloWorld sample:
```
 wget https://raw.githubusercontent.com/bgaster/opencl-book-samples/master/src/Chapter_2/HelloWorld/HelloWorld.cpp
 wget https://raw.githubusercontent.com/bgaster/opencl-book-samples/master/src/Chapter_2/HelloWorld/HelloWorld.cl
```

 Build it using the default ROCm OpenCL include and library locations:
```
g++ -I /opt/rocm/opencl/include/ ./HelloWorld.cpp -o HelloWorld -L/opt/rocm/opencl/lib/x86_64 -lOpenCL
```

 Run it:
 ```
 ./HelloWorld
```

##### Un-install ROCm 
To un-install the entire rocm development package execute:
* Ubuntu 
```shell
sudo apt-get autoremove rocm-dkms



### Installing development packages for cross compilation

It is often useful to develop and test on different systems. In this scenario, you may prefer to avoid installing the ROCm Kernel to your development system.

In this case, install the development subset of packages:

```shell
sudo apt-get update
sudo apt-get install rocm-dev
```
