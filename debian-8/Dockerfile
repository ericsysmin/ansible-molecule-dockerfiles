FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive

RUN sed -i s/deb.debian.org\\/debian\ jessie-updates/archive.debian.org\\/debian\ jessie/g /etc/apt/sources.list
RUN sed -i s/deb.debian.org\\/debian\ jessie/archive.debian.org\\/debian\ jessie/g /etc/apt/sources.list
RUN sed -i s/security.debian.org\\/debian-security\ jessie/archive.debian.org\\/debian-security\ jessie/g /etc/apt/sources.list

RUN apt-key update && apt-get update \
  && apt-get install -y --no-install-recommends sudo build-essential \
    libffi-dev libssl-dev \
    python-pip python-dev \
  && rm -rf /var/lib/apt/lists/* \
  && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
  && apt-get clean

VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]
