# Dockerfile creada para el curso de redes neuronales
# Universidad de Sonora, Licenciatura en Ciencias de la Computación
# Ultima modificación: 16 enero de 2018
# Elaborado por J. Waissman, basado en las dockerfiles de Tensorflow y las propias

# Este dockerfile solamente genera imágenes para CPU, es necesario instalar 
# lo correspondiente para ejecutar en el servidor

FROM ubuntu:16.04 AS base
LABEL maintainer="Julio Waissman <julio.waissman@unison.mx>"

#
# Actualiza el SO e instala librerías necesarias
#
RUN apt-get update && apt-get install -yq \
            build-essential \
            curl \
            git \
            wget \
            graphviz \
            vim \
            htop \
            unzip \
            zip \
            openjdk-8-jdk \
            openjdk-8-jre-headless \
    && \
    apt-get clean 

#
# Entornos
#
ENV CI_BUILD_PYTHON python
ENV LANG C.UTF-8

#
# Instala python3 y actualiza
#
RUN apt-get update && apt-get install -yq \
    python3 \
    python3-pip

RUN pip3 --no-cache-dir install --upgrade \
    pip \
    setuptools

RUN ln -s $(which python3) /usr/local/bin/python

#
# Instala los móduos más interesantes para redes neuronales
#
RUN pip3 install \
    Pillow \
    requests \
    pyyaml \
    pydot \
    h5py \
    matplotlib \
    numpy \
    scipy \
    sklearn \
    pandas \
    tensorflow \
    keras \
    jupyter

#
# Instala las extensiones de jupyter y lo configura
#

RUN pip3 install jupyter_contrib_nbextensions
RUN jupyter nbextension enable --py --sys-prefix widgetsnbextension
RUN jupyter contrib nbextension install
RUN jupyter nbextension enable codefolding/main
RUN echo "c.NotebookApp.ip = '*'" >> /root/.jupyter/jupyter_notebook_config.py
RUN echo "c.NotebookApp.port = 8080" >> /root/.jupyter/jupyter_notebook_config.py
RUN echo "c.NotebookApp.token = ''" >> /root/.jupyter/jupyter_notebook_config.py
RUN echo "jupyter notebook --no-browser --allow-root" >> /usr/local/bin/run_notebook && chmod +x /usr/local/bin/run_notebook

#
# Iniciacliza .bashrc con saludos y demás
#
COPY bashrc /etc/bash.bashrc
RUN chmod a+rwx /etc/bash.bashrc

#
# Instala los ejemplos de tensorflow
#
RUN mkdir -p /curso-rn/tutoriales-tensorflow && chmod -R a+rwx /curso-rn/
RUN mkdir /.local && chmod a+rwx /.local

WORKDIR /tf/tutoriales-tensorflow

RUN wget https://raw.githubusercontent.com/tensorflow/docs/master/site/en/tutorials/keras/basic_classification.ipynb
RUN wget https://raw.githubusercontent.com/tensorflow/docs/master/site/en/tutorials/keras/basic_regression.ipynb
RUN wget https://raw.githubusercontent.com/tensorflow/docs/master/site/en/tutorials/keras/basic_text_classification.ipynb
RUN wget https://raw.githubusercontent.com/tensorflow/docs/master/site/en/tutorials/keras/save_and_restore_models.ipynb
RUN wget https://raw.githubusercontent.com/tensorflow/docs/master/site/en/tutorials/keras/save_and_restore_models.ipynb

#
# Expone al SO original el puerto 8080 para poder usar jupyter
#
EXPOSE 8080

#
# Iniciliza el directorio de trabajo en curso-rn y ejecuta
#
RUN python3 -m ipykernel.kernelspec
WORKDIR /curso-rn

CMD ["bash", "-c", "source /etc/bash.bashrc"]

