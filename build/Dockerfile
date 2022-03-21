#docker run -p 8888:8888 -v `pwd`:`pwd` -it --rm --gpus all  py3d python jupyter notebook --allow-root --ip=0.0.0.0 --no-browser


#FROM tensorflow/tensorflow:2.0.0-gpu-py3-jupyter
#FROM tensorflow/tensorflow:2.7.1-gpu-jupyter
FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04

WORKDIR /build
RUN apt-get update -y
RUN apt-get install -y wget
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ./miniconda.sh
RUN bash miniconda.sh -b -p /root/miniconda
SHELL ["/bin/bash", "-c"]
RUN /root/miniconda/bin/conda init
RUN source /root/.bashrc
ENV PATH /root/miniconda/bin:$PATH

RUN apt-get update
RUN apt-get install -y vim

RUN conda update --all

#####
COPY environment.yml environment.yml

RUN conda update conda
#RUN conda env create --name pytorch3d --file environment.yml
####
RUN conda create -y -n pytorch3d python=3.9
RUN echo "conda activate pytorch3d" >> /root/.bashrc


#RUN conda install --name pytorch3d --yes -c pytorch pytorch=1.9.1 torchvision cudatoolkit=10.2

#RUN conda install --name pytorch3d --yes -c fvcore -c iopath -c conda-forge fvcore iopath

#RUN conda install --name pytorch3d --yes -c bottler nvidiacub

#RUN conda install --name pytorch3d --yes jupyter

#RUN /bin/bash -c ". activate pytorch3d && \
#    pip install --upgrade pip && \
#    pip install \
#    scikit-image \
#    matplotlib \
#    imageio \
#    black \
#    isort \
#    flake8 \
#    flake8-bugbear \
#    flake8-comprehensions plotly opencv-python"

#RUN /bin/bash -c ". activate pytorch3d && \
#    pip install black 'isort<5' flake8 flake8-bugbear flake8-comprehensions"

RUN conda install --name pytorch3d --yes pytorch3d -c pytorch -c fvcore -c conda-forge -c defaults -c pytorch3d-nightly

RUN conda install --name pytorch3d --yes jupyter
RUN /bin/bash -c ". activate pytorch3d && pip install matplotlib numpy-quaternion scipy numba"
