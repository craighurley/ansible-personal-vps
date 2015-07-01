#{{ ansible_managed }}

FROM        centos:centos7
MAINTAINER  Craig Hurley

# Install ZNC
RUN         yum -y update && \
            yum -y install epel-release && \
            yum -y install znc && \
            yum clean all

# Generate SSL key
RUN         mkdir -p /var/lib/znc/.znc
RUN         znc -d /var/lib/znc/.znc -p
RUN         chown -R znc:znc /var/lib/znc

EXPOSE      6697

USER        znc

VOLUME      ["/var/lib/znc/.znc"]

CMD         ["znc", "-f"]
