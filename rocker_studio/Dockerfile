# vi Dockerfile
FROM rocker/rstudio:4

RUN apt update
ENV DISABLE_AUTH=true
RUN apt install libudunits2-dev ffmpeg libsm6 libxext6 libproj-dev libgdal-dev libxt6 -y
