#
# TreasureBoat.org
# by ishimoto
#
# sshd service on CentOS 6.6
#
# build : docker build -t treasureboat/ssh:0.3 .
# run : docker run -d -P --name tbSSH treasureboat/ssh:0.3

FROM treasureboat/centos6:latest
MAINTAINER treasureboat <ken@ksroom.com>

# this is the Open SSH Server
RUN yum install -y openssh-server

# this will add the 'scp' command
RUN yum install -y openssh-clients

#generate ssh key
RUN ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key
RUN ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key
RUN sed -ri 's/session required pam_loginuid.so/#session required pam_loginuid.so/g' /etc/pam.d/sshd
RUN mkdir -p /root/.ssh && chown root.root /root && chmod 700 /root/.ssh

#change root password to 123456
RUN echo 'root:123456' | chpasswd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
