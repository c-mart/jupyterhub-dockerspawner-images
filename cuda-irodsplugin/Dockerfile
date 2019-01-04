FROM nvidia/cuda:10.0-devel

RUN apt-get update

# Get npm required for Jupyter Lab extensions
# https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04
RUN apt-get -y install npm


RUN apt-get -y install python3-pip
RUN pip3 install \
    jupyterhub==0.9.4 \
    'notebook>=5.0,<=6.0' \
    jupyterlab \
    jupyterlab_irods \
    pycuda
# From https://github.com/towicode/IJab
RUN jupyter serverextension enable --py jupyterlab_irods
RUN jupyter labextension install ijab

# create a user, since we don't want to run as root
RUN useradd -m jovyan
ENV HOME=/home/jovyan
WORKDIR $HOME
USER jovyan


CMD ["jupyterhub-singleuser"]
