# TensorFlow

## ROCm Tensorflow v1.10 Release
We are excited to announce the release of ROCm enabled TensorFlow v1.11 for AMD GPUs.

### Tensorflow Installation
First, you’ll need to install the open-source ROCm stack, require at least ROCm1.9.0. Details can be found here: https://rocm.github.io/ROCmInstall.html
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
Now that Tensorflow v1.11 is installed!

### Tensorflow More Resources
Tensorflow docker images are also publicly available, more details can be found here:
https://hub.docker.com/r/rocm/tensorflow/

Please connect with us for any questions, our official github repository is here:
https://github.com/ROCmSoftwarePlatform/tensorflow-upstream

