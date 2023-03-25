# vi Dockerfile
FROM python:3.9

RUN apt-get update
RUN pip install --upgrade pip
RUN python -m pip install jupyterlab
COPY requirement.txt /
RUN pip install -r requirement.txt