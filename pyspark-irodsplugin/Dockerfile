FROM jupyter/pyspark-notebook:a95cb64dfe10

USER root

RUN apt-get update

# Get npm required for Jupyter Lab extensions
# https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04
RUN apt-get -y install npm

# RUN apt-get -y install python3-pip
RUN conda install pip
RUN pip install \
    jupyterlab \
    jupyterlab_irods
# From https://github.com/towicode/IJab
RUN jupyter serverextension enable --py jupyterlab_irods
RUN jupyter labextension install ijab
RUN jupyter labextension install @jupyterlab/hub-extension

USER jovyan


CMD ["jupyterhub-singleuser"]
