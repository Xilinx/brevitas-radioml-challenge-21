# Sandbox: Lightning-Fast Modulation Classification with Hardware-Efficient Neural Networks

This repository provides a Docker-based environment to get started with the [Lightning-Fast Modulation Classification with Hardware-Efficient Neural Networks](https://challenge.aiforgood.itu.int/match/matchitem/34) problem statement of the [**ITU AI/ML in 5G Challenge**](https://aiforgood.itu.int/ai-ml-in-5g-challenge/). The sandbox environment includes PyTorch and Brevitas and serves a Jupyter notebook that guides you through definition, training, and evaluation of an exemplary quantized CNN model.

## Prerequisites

The sandbox was tested on Ubuntu, but the containerized setup should work on most platforms.

- Install Docker Engine
  - Convenient install script: [get.docker.com](https://get.docker.com)
  - Full installation instructions:  [docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)
  - To use docker without `sudo` you should follow these [instructions](https://docs.docker.com/engine/install/linux-postinstall/) to add your user to the `docker group`
- Optional steps to enable GPU-accelerated training (recommended)
  - Install current NVIDIA driver
  - Install NVIDIA Container Toolkit, see instructions here: [github.com/NVIDIA/nvidia-docker](https://github.com/NVIDIA/nvidia-docker)

## Using the sandbox notebook

1. Clone this repository
2. Set optional environment variables
   - `DATASET_DIR`: This directory will be mounted inside the container at "/workspace/dataset", download instructions can be found inside the Jupyter notebook
   - `DOCKER_GPUS`: Select GPUs which will be accessible from within the container, for example `all` or `device=0`
   - `JUPYTER_PORT`: Override default port (8888)
   - `NETRON_PORT`: Override default port (8081)
   - `JUPYTER_PASSWD_HASH`: Override default password ("radioml")
   - `LOCALHOST_URL`: Set the IP/URL of the machine if you don't access it via `localhost`
3. Run `./run_docker.sh` inside `sandbox/` to launch the Jupyter notebook server
   - Alternatively for experimenting: Run `./run_docker.sh bash` to launch an interactive shell
4. Connect to `http://HOSTNAME:JUPYTER_PORT` from a browser and login with password "radioml"

## Getting help
Connect with the challenge organizers and other participants on [GitHub discussion](https://github.com/Xilinx/brevitas-radioml-challenge-21/discussions). For questions related to quantization-aware training with Brevitas, there is also a separate Gitter channel: [![Gitter](https://badges.gitter.im/xilinx-brevitas/community.svg)](https://gitter.im/xilinx-brevitas/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
 