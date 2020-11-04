FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive
ARG workdir="/root"
COPY ./sources.list  /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
	nginx	\
	python3-jinja2	\
	python3-pyinotify	\
	python3-requests	\
	&& rm -rf /etc/nginx/sites-enabled/default

# add Config Render
ADD templates ${workdir}/templates
ADD config-render.py ${workdir}/config-render.py

# add kick-update
ADD kick-update.py ${workdir}/kick-update.py
ADD ./nante-wan.conf /etc/nante-wan.conf

CMD bash -c "/root/config-render.py /etc/nante-wan.conf && nginx && /root/kick-update.py -c /etc/nante-wan.conf -d /var/www/html"
