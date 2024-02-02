FROM debian:stretch

ENV DEBIAN_FRONTEND noninteractive

RUN sed -i s/deb.debian.org\\/debian\ stretch-updates/archive.debian.org\\/debian\ stretch/g /etc/apt/sources.list
RUN sed -i s/deb.debian.org\\/debian\ stretch/archive.debian.org\\/debian\ stretch/g /etc/apt/sources.list
RUN sed -i s/security.debian.org\\/debian-security\ stretch/archive.debian.org\\/debian-security\ stretch/g /etc/apt/sources.list

RUN apt-key update && apt-get update \
  && apt-get install -y --no-install-recommends sudo systemd systemd-sysv \
     build-essential wget libffi-dev libssl-dev \
     python-pip python-dev python-setuptools python-wheel \
  && rm -rf /var/lib/apt/lists/* \
  && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
  && apt-get clean

# Make sure systemd doesn't start agettys on tty[1-6].
RUN rm -f /lib/systemd/system/multi-user.target.wants/getty.target

VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]
