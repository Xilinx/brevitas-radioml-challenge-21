# brevitas-radioml-challenge-21

## Prerequisites

The following steps were tested on Ubuntu, but the containerized setup should work on most platforms.

- Install Docker Engine
  - Convenient install script: https://get.docker.com
  - Full installation instructions: https://docs.docker.com/engine/install/
  - You should add your user to the `docker` group to allow access without `sudo`, see https://docs.docker.com/engine/install/linux-postinstall/

Optional steps to enable GPU acceleration for training:

- Install current NVIDIA driver
- Install NVIDIA Container Toolkit, see instructions here: https://github.com/NVIDIA/nvidia-docker

## Using the sandbox notebook

- Clone this repository
- Set optional environment variables
  - `DATASET_PATH`: This directory will be mounted inside the container under "/workspace/dataset", download instructions can be found inside the Jupyter notebook
  - `DOCKER_GPUS`: Select which GPUs will be accessible from within the container, for example `all` or `device=0`
  - `JUPYTER_PORT`: Override default port (8888)
  - `NETRON_PORT`: Override default port (8081)
  - `JUPYTER_PASSWD_HASH`: Override default password ("radioml")
- **Run `./run_docker.sh` inside `sandbox/` to launch the Jupyter notebook server**
- **Connect to `http://HOSTNAME:JUPYTER_PORT` from a browser and login with password "radioml"**
- Alternatively (for experimentation): Run `./run_docker.sh bash` to launch an interactive shell
