FROM ubuntu:lucid
MAINTAINER Honglin Feng <hfeng@tutum.co>

# Install packages
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get -y install openssh-server pwgen nano
RUN mkdir -p /var/run/sshd && sed -i "s/UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config && sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config && sed -i "s/PermitRootLogin.*/PermitRootLogin yes/g" /etc/ssh/sshd_config

ADD set_root_pw.sh /set_root_pw.sh
ADD run.sh /run.sh
RUN chmod +x /*.sh

ENV ROOT_PASS **ChangeMe**
ENV AUTHORIZED_KEYS **None**

EXPOSE 22
CMD ["/run.sh"]
