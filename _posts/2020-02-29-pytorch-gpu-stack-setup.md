---
layout: post
title: "PyTorch GPU Stack in 5 minutes or less"
subtitle: "Fast setup for a PyTorch stack on GPU with CUDA + CUDNN"
description: Steps using Docker containers for a PyTorch deep learning stack on GPU with CUDA + CUDNN.
permalink: pytorch-gpu-stack-setup
image: /img/pytorch-stack-icon.jpg
tags: [pytorch, deep learning, gpu, docker, cuda, cudnn]
published: true
---

Historically, setting up deep learning stacks with GPU support has been a hassle.
This was because of poorly documented version conflicts between NVIDIA drivers, CUDA, CUDNN and your DL library of choice (PyTorch and TF for me).
I remember having spent hours on setting up Tensorflow because its docs didn't say which NVIDIA driver was required.
Documentation these days is miles better but often omits one of the most user-friendly ways of developing for Deep Learning: containers.

{% include image.html
            img="/img/pytorch-stack.jpg"
            title="PyTorch + CUDA + CUDNN stack in Docker"
            caption="Stacked and ready to roll." %}

Recently, Docker v19.03 has received full support for NVIDIA GPUs (before you had to use NVIDIA's custom fork.)

People have been rolling their own containers with PyTorch + CUDA + CUDNN for [quite](https://github.com/anibali/docker-pytorch) [some time](https://hub.docker.com/r/ceshine/cuda-pytorch/) now.
But little known is that an official release exists of PyTorch with the GPU stack.
Presumably, the existence of a CUDA-enabled container is little known because it is undocumented in [the official PyTorch documentation](https://pytorch.org/docs/stable/index.html) and is hidden behind the Tags section of [the PyTorch Docker Hub repo](https://hub.docker.com/r/pytorch/pytorch/).

NVIDIA GPU Cloud also has a PyTorch image but requires new GPUs with a CUDA Compute Capability of 6.0+.
My Tesla K80 DL and Pascal V100 equipped servers fall below that and my poor notebook only has an 840M with CC 3.5.
The NVIDIA GPU Cloud image will detect your GPU and CUDA just fine but will fail when trying to actually use the device.
If you're running into `Cuda error: no kernel image is available for execution on the device` when trying to load Tensors on your GPU with those images.
That's the undocumented reason.

## Requirements
- Docker v19.03: [Installation instructions here](https://docs.docker.com/install/).
- NVIDIA driver: Probably already installed but [official instructions here](https://www.nvidia.com/Download/).

## Steps
1. Pull the prebuilt PyTorch Docker image with CUDA + CUDNN: <br/>Go to [Tags tab of the PyTorch Docker Hub page](https://hub.docker.com/r/pytorch/pytorch/tags), select the latest developer image (ends in `devel`) which has CUDA and CUDNN in the name:
  <br/>`docker pull pytorch/pytorch:1.4-cuda10.1-cudnn7-devel`

2. Run the images: <br/>`docker run --gpus all -it --rm --ipc=host -v /localdir/:/containerdir/ --name mypytorchproject pytorch/pytorch:1.4-cuda10.1-cudnn7-devel`
  - `--gpus all` Use all available CUDA enabled GPUs. Use `--gpus '"device=0,1"'` to specify specific gpus.
  - `--it` means it will run in interactive mode.
  - `--rm` will delete the container when finished.
  - `--ipc==host` Use the host's inter-process communication namespace in using shared memory. If you use Torch multiprocessing for multi-threaded data loaders, the default shared memory segment size that the container runs with may not be enough. Therefore, you should increase the shared memory size with this option. You can also manually set the size with `--shm-size=`.
  - `--v /local_dir/:/container_dir/`: local_dir is the directory or file from your host system (absolute path) that you want to access from inside your container. Mount your project directory here with code and data to work on it from inside the container at the /containerdir/ path. 
  - `--name mypytorchproject` assign a name the container for future reference so you can simply type `docker start mypytorchproject` to start the container with these run settings.

3. Test if your container truly is using CUDA-enabled GPU:
  ```
  $ python -c "import torch; device = torch.device('cuda' if torch.cuda.is_available() else 'cpu'); print('Using device:', device); torch.rand(10).to(device)"
  > Using device: cuda
  ```

You're done, a deep learning stack that just works!
