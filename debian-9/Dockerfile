FROM debian:9

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
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
