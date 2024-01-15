FROM debian:bullseye

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
  && apt-get install -y --no-install-recommends sudo systemd systemd-sysv \
    build-essential wget libffi-dev libssl-dev \
    python3-pip python3-dev python3-setuptools python3-wheel \
  && rm -rf /var/lib/apt/lists/* \
  && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
  && apt-get clean

# Make sure systemd doesn't start gettys on tty
RUN rm -f /lib/systemd/system/multi-user.target.wants/getty.target

VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]
