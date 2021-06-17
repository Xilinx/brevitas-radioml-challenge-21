# Copyright (c) 2020, Xilinx
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#
# * Redistributions of source code must retain the above copyright notice, this
#   list of conditions and the following disclaimer.
#
# * Redistributions in binary form must reproduce the above copyright notice,
#   this list of conditions and the following disclaimer in the documentation
#   and/or other materials provided with the distribution.
#
# * Neither the name of FINN nor the names of its
#   contributors may be used to endorse or promote products derived from
#   this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
# DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
# FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
# SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
# CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
# OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

FROM pytorch/pytorch:1.7.1-cuda11.0-cudnn8-runtime
#FROM pytorch/pytorch:1.6.0-cuda10.1-cudnn7-runtime
LABEL maintainer="Yaman Umuroglu <yamanu@xilinx.com>"
ARG GID
ARG GNAME
ARG UNAME
ARG UID
ARG PASSWD

WORKDIR /workspace

RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get install -y build-essential
RUN apt-get install -y libglib2.0-0
RUN apt-get install -y libsm6
RUN apt-get install -y libxext6
RUN apt-get install -y libxrender-dev
RUN apt-get install -y nano
RUN apt-get install -y zsh
RUN apt-get install -y rsync
RUN apt-get install -y git
RUN apt-get install -y sshpass
RUN apt-get install -y wget
RUN apt-get install -y unzip
RUN apt-get install -y zip
RUN echo "StrictHostKeyChecking no" >> /etc/ssh/ssh_config

RUN pip install future==0.18.2
RUN pip install numpy==1.18.0
RUN pip install scipy==1.5.2
RUN pip install jupyter==1.0.0
RUN pip install matplotlib==3.3.1 --ignore-installed
RUN pip install netron>=4.7.9
RUN pip install pandas==1.1.5
RUN pip install scikit-learn==0.24.1
RUN pip install tqdm==4.61.1
RUN pip install dill==0.3.3
RUN pip install -e git+https://github.com/fbcotter/dataset_loading.git@0.0.4#egg=dataset_loading

RUN pip install brevitas==0.5.1
#RUN pip install onnx==1.8.1
RUN pip install onnxoptimizer==0.2.6

#RUN pip install clize==4.1.1
#RUN pip install onnxruntime==1.4.0
#RUN pip install toposort>=1.5.0
RUN pip install git+https://github.com/Xilinx/finn-base.git@feature/qonnx_compute_cost#egg=finn-base[onnx]

RUN pip install versioned-hdf5

# switch user
RUN groupadd -g $GID $GNAME
RUN useradd -M -u $UID $UNAME -g $GNAME
RUN usermod -aG sudo $UNAME
RUN echo "$UNAME:$PASSWD" | chpasswd
RUN echo "root:$PASSWD" | chpasswd
RUN chown -R $UNAME:$GNAME /workspace
RUN ln -s /workspace /home/$UNAME
USER $UNAME

WORKDIR /home/$UNAME/finn

CMD ["bash"]
