FROM nvidia/cuda:10.0-devel
RUN pip3 install \
    jupyterhub==0.7.2 \
    'notebook>=5.0,<=6.0' \
    jupyterlab_irods
RUN jupyter serverextension enable --py jupyterlab_irods
RUN jupyter labextension install ijab

# create a user, since we don't want to run as root
RUN useradd -m jovyan
ENV HOME=/home/jovyan
WORKDIR $HOME
USER jovyan

CMD ["jupyterhub-singleuser"]
