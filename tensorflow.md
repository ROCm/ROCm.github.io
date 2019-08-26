# TensorFlow

## Tensorflow Community Supported Build for ROCm is ready!
We are excited to announce that official Tensorflow now includes Linux AMD ROCm GPU nightly builds.
Link to the upstream Tensorflow CSB doc: https://github.com/tensorflow/tensorflow#community-supported-builds

### Tensorflow CSB Installations
Tensorflow CSB builds are currently supoprted ROCm Version 2.6
We provide nightly tensorflow-rocm whl packages for Python 2.7, 3.5, 3.6 and 3.7 based systems.
After downloading the compatible whl package, you can use pip/pip3 to install.
For example, the following commands can be used to download and install the tensorflow-rocm CSB package on an Ubuntu 16.04 system configured with ROCm 2.6 and Python3.5:
```
wget http://ml-ci.amd.com:21096/job/tensorflow-rocm-release/lastSuccessfulBuild/artifact/pip35_test/whl/tensorflow_rocm-1.14.0-cp35-cp35m-manylinux1_x86_64.whl
pip3 install --user tensorflow_rocm-1.14.0-cp35-cp35m-manylinux1_x86_64.whl
```
For details, please refer to the following document for more installation instructions:
https://github.com/ROCmSoftwarePlatform/tensorflow-upstream/blob/develop-upstream/rocm\_docs/tensorflow-install-basic.md

## ROCm Tensorflow Official Releases
Tensorflow official releases now support v1.14.1 and v2.0-beta-v3 on ROCm2.7
Please refer to the following document for more details:
https://github.com/ROCmSoftwarePlatform/tensorflow-upstream/blob/develop-upstream/RELEASE.md

### Tensorflow Installation
First, you’ll need to install the open-source ROCm stack. Details can be found here: https://rocm.github.io/ROCmInstall.html
Then, install these other relevant ROCm packages:
```
sudo apt update
sudo apt install rocm-libs miopen-hip cxlactivitylogger
```
And finally, install TensorFlow itself (via the Python Package Index):
```
sudo apt install wget python3-pip
# Pip3 install the whl package from PyPI
pip3 install --user tensorflow-rocm
```
Now that Tensorflow v1.14.1 is installed!

### Tensorflow More Resources
Tensorflow docker images are also publicly available, more details can be found here:
https://hub.docker.com/r/rocm/tensorflow/

Please connect with us for any questions, our official github repository is here:
https://github.com/ROCmSoftwarePlatform/tensorflow-upstream
