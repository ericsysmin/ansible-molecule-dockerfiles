FROM centos:6

RUN yum makecache fast \
  && yum -y install deltarpm epel-release \
  && yum -y update \
  && yum -y install ansible sudo which initscripts python-urllib3 pyOpenSSL \
   python2-ndg_httpsclient python-pyasn1 \
  && yum clean all

# Disable requiretty.
RUN sed -i -e 's/^\(Defaults\s*requiretty\)/#--- \1/'  /etc/sudoers

CMD ["/sbin/init"]
