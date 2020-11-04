FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive
ARG workdir="/root"
COPY ./sources.list  /etc/apt/sources.list

# install required packages
RUN apt-get update && apt-get install -y \
	iproute2 python3 python3-requests python3-flask


# setup sdwconfig
ADD portconfig.py ${workdir}/portconfig.py
ADD ./nante-wan.conf /etc/nante-wan.conf
CMD bash -c "/root/portconfig.py /etc/nante-wan.conf"
