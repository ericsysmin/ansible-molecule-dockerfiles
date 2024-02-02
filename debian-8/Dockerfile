FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive

RUN sed -i s/deb.debian.org\\/debian\ stretch-updates/archive.debian.org\\/debian\ stretch/g /etc/apt/sources.list
RUN sed -i s/deb.debian.org\\/debian\ stretch/archive.debian.org\\/debian\ stretch/g /etc/apt/sources.list
RUN sed -i s/security.debian.org\\/debian-security\ stretch/archive.debian.org\\/debian-security\ stretch/g /etc/apt/sources.list

RUN apt-get update \
  && apt-get install -y --no-install-recommends sudo build-essential \
    libffi-dev libssl-dev \
    python-pip python-dev \
  && rm -rf /var/lib/apt/lists/* \
  && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
  && apt-get clean

VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]
