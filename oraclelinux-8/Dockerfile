FROM oraclelinux:8
ENV container=docker

# Install systemd -- See https://hub.docker.com/_/centos/
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

RUN yum -y update \
  && yum -y install http://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm \
  && yum -y install initscripts sudo which hostname \
    python3 python3-pip

# Disable requiretty.
RUN sed -i -e 's/^\(Defaults\s*requiretty\)/#--- \1/'  /etc/sudoers

VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/lib/systemd/systemd"]
