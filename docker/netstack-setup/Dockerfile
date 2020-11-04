FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive
ARG workdir="/root"
COPY ./sources.list  /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
	python3 iproute2 iptables kmod

ADD start.py ${workdir}/start.py
ADD ./nante-wan.conf /etc/nante-wan.conf

CMD [ "python3", "/root/start.py", "--network-only", "/etc/nante-wan.conf" ]
