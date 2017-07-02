---
layout: default
title: ROCm Install
---

## ROCm GPU Server Driver Installation Guide for Linux 

### Introduction 
The ROCm Platform brings a rich foundation to advanced computing by seamlessly integrating the CPU and GPU with the goal of solving real-world problems.

This support starts with AMD’s FIJI Family of dGPUs. ROCm 1.3 further extends support to include the Polaris Family of ASICs. With ROCm 1.6 we add Vega Family of products. 

### System Requirements 

To use ROCm on your system you need the following: 
* ROCm Capable CPU and GPU 
	* PCIe Gen 3 Enabled CPU with PCIe Platform Atomics 
	* ROCm enabled GPU's 
		* Radeon Instinct Family MI25, MI8, MI6 
		* Radeon Vega Frontier Edition 
* Supported Version of Linux with a specified GCC Compiler and ToolChain 


Table 1. Native Linux Distribution Support in ROCm  1.6

|Distribution	|Kernel	|GCC	|GLIBC	|
|:--------------|:------|:------|:------|
|x86_64		|	|	|       |
|Fedora 24 	|4.9	|5.40	|2.23   |		
|Ubuntu 16.04	|4.9	|5.40	|2.23   |		
	
### Pre Install Directions 

#####Verify You Have ROCm Capable GPU Installed int the System 

```shell
lspci | grep -i AMD
```
######You will see list of AMD GPU's 

##### Verify You Have a Supported Version of Linux 

```shell
uname - m && cat /etc/*release
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

```shell
sudo apt-get update
sudo apt-get install rocm rocm-opencl-dev
```

Then, make the ROCm kernel your default kernel. If using grub2 as your bootloader, you can edit the GRUB_DEFAULT variable in the following file:

```shell
sudo nano /etc/default/grub
```
set the GRUB_Default 
Edit: GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 4.9.0-kfd-compute-rocm-rel-1.6-77"
```shell
sudo update-grub
```
------------------------------------

#### Fedora Install 
Use the  dnf (yum) repository for installation of rpm packages.
To configure a system to use the ROCm rpm directory create the file
/etc/yum.repos.d/rocm.repo with the following contents:

```shell
[remote]

name=ROCm Repo

baseurl=http://repo.radeon.com/rocm/yum/rpm/

enabled=1

gpgcheck=0
```

Execute the following commands:
```shell
sudo dnf clean all
sudo dnf install rocm rocm-opencl-dev
```
Just like Ubuntu installs, the ROCm kernel must be the default kernel used at boot time.

Post Install Manual installation steps for Fedora to support HCC compiler 

A fully functional Fedora installation requires a few manual steps to properly 
setup, including:
 * [Building compatible libc++ and libc++abi libraries for Fedora](https://github.com/RadeonOpenCompute/hcc/wiki#fedora)



##### Post install verification 

Verify you have the correct Kernel Post install 

```shell
$ uname -r
4.9.0-kfd-compute-rocm-rel-1.6-77
```

Test the driver is installed correctly 
```shell
cd /opt/rocm/hsa/sample
make
./vector_copy
```
Test if OpenCL is working based on default ROCm OpenCL include and library locations:
```shell
g++ -I /opt/rocm/opencl/include/ ./HelloWorld.cpp -o HelloWorld -L/opt/rocm/opencl/lib/x86_64 -lOpenCL
```

Run it:
```shell
./HelloWorld
```

### To Uninstall the a Package 
* Ubuntu 
```shell
sudo apt-get purge libhsakmt
sudo apt-get purge radeon-firmware
sudo apt-get purge $(dpkg -l | grep 'kfd\|rocm' | grep linux | grep -v libc | awk '{print $2}')
```
* Fedora 
```shell
sudo dnf remove ROCm   
```	
[List of ROCm Packages for Ubuntu and Fedora](ROCmLinuxpackages.md)

### Installing development packages for cross compilation

It is often useful to develop and test on different systems. In this scenario, you may prefer to avoid installing the ROCm Kernel to your development system.

In this case, install the development subset of packages:

```shell
sudo apt-get update
sudo apt-get install rocm-dev
```
