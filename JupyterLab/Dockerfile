# vi Dockerfile
FROM python:3.9

RUN apt-get update
RUN apt-get install --no-install-recommends npm -y
RUN apt-get install --no-install-recommends nodejs -y

RUN pip install --upgrade pip
RUN python -m pip install jupyterlab

# 日本語化
RUN pip install jupyterlab-language-pack-ja-JP

# autocomplete
# RUN pip install jupyterlab_tabnine

# lckr/jupyterlab_variableinspector
RUN pip install lckr-jupyterlab-variableinspector==3.0.7

# jupyterlab-lsp
RUN pip install jupyterlab-lsp
RUN pip install 'python-lsp-server[all]'

# jupyter-lab-code-formatter
RUN pip install jupyterlab-code-formatter

# black
RUN pip install black

##
RUN pip install pandas
