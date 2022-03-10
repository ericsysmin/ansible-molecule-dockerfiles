FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
  && apt-get install -y --no-install-recommends sudo build-essential \
    libffi-dev libssl-dev \
    python-pip python-dev \
  && rm -rf /var/lib/apt/lists/* \
  && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
  && apt-get clean

VOLUME ["/sys/fs/cgroup"]
CMD ["/lib/systemd/systemd"]
