#{{ ansible_managed }}

FROM centos:centos7
MAINTAINER Craig Hurley

# Install ZNC
RUN yum -y update ; yum -y install epel-release
RUN yum -y install znc ; yum clean all

# ADD

# Generate SSL key
RUN znc -d /var/lib/znc/.znc -p

# RUN systemctl enable znc
# RUN systemctl start znc

EXPOSE 6697

USER znc
