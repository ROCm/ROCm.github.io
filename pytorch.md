# PyTorch

### General remarks

This is a quick guide to run PyTorch with ROCm support inside a provided docker image.  Assumes a .deb based system. See [ROCm install](https://rocm.github.io/ROCmInstall.html) for supported operating systems and general information on the ROCm software stack.

A ROCm install version 2.1 is required currently.

A Vega10 / gfx900 generation discrete graphics card is required (Vega56, Vega64, or MI25).

The image contains hipified PyTorch source, a clone of the PyTorch examples, and has PyTorch for gfx900 installed.

1) **Install or update rocm-dev on the host system:**<br>
`sudo apt-get install rocm-dev`<br>
or<br>
`sudo apt-get update`<br>
`sudo apt-get upgrade`<br>

2) **Obtain docker image:**<br>
`docker pull rocm/pytorch:rocm2.1_ubuntu16.04_pytorch_gfx900`

4) **Start a docker container using the downloaded image:**<br>
`sudo docker run -it -v $HOME:/data --privileged --rm --device=/dev/kfd --device=/dev/dri --group-add video rocm/pytorch:rocm2.1_ubuntu16.04_pytorch_gfx900`<br>
Note: This will mount your host home directory on `/data` in the container.

5) **Confirm working setup:**<br>
   `cd ~/pytorch`
   `PYTORCH_TEST_WITH_ROCM=1 python test/run_test.py --verbose`<br>
   No tests will fail if the setup is correct and hardware is supported.

6) **Run individual example: MNIST**<br>
   `cd ~/examples/mnist`<br>
   Follow instructions in `README.md`, in this case:<br>
   `pip install -r requirements.txt`
   `python main.py`
7) **Run individual example: Try ImageNet training** <br>
   `cd ~/examples/imagenet`<br>
   Follow instructions in `README.md`.

## Running PyTorch with Caffe2 backend
1) **Obtain docker image:**<br>
`docker pull rocm/pytorch:rocm2.1_caffe2`<br>
This image has Caffe2 installed and works for gfx900 and gfx906 architectures.<br>

2) **Start a docker container using the downloaded image:**<br>
`sudo docker run -it -v $HOME:/data --privileged --rm --device=/dev/kfd --device=/dev/dri --group-add video rocm/pytorch:rocm2.1_caffe2`<br>
Note: This will mount your host home directory on `/data` in the container.

3) **Confirm working setup:**<br>
`cd ~ && python -c 'from caffe2.python import core' 2>/dev/null && echo "Success" || echo "Failure"`<br>

4) **Runing benchmarks:**<br>
Caffe2 benchmarking script supports the following networks *MLP, AlexNet, OverFeat, VGGA, Inception. To run benchmarks for networks MLP, AlexNet, OverFeat, VGGA, Inception run the command from pytorch home directory replacing `<name_of_the_network>` with one of the networks. <br>
`cd /pytorch`<br>
`python caffe2/python/convnet_benchmarks.py --batch_size 64 --model <name_of_the_network> --engine MIOPEN`<br>

5) **Running example scripts:**<br>
Please refer to the example scripts in `caffe2/python/examples`. It currently has `resnet50_trainer.py` which can run ResNet's, ResNeXt's with various layer, groups, depth configurations and `char_rnn.py` which uses RNNs to do character level prediction.
An example resnet50_trainer command would like this:<br>
`python caffe2/python/examples/resnet50_trainer.py --train_data <path_to_train_data> --test_data <path_to_test_data> --batch_size 32 --epoch_size 32000 --num_epochs 10 --num_gpus 2`<br>
