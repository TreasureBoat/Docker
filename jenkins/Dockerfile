#
# TreasureBoat.org
# by ishimoto
#
# Jenkins 1.596 on CentOS 6.6
#
# service jenkins start/stop/restart
#
# build : docker build -t treasureboat/jenkins:0.2 .
# run development : docker run -d -P --name tbJenkins treasureboat/jenkins:0.2
# run deploy : docker run -d -p 8080:8080 --name tbJenkins -it treasureboat/jenkins:0.2

FROM treasureboat/java:latest
MAINTAINER treasureboat <office@treasureboat.org>

##### download jenkins get latest and greatest
#RUN wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
#RUN rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
#RUN yum install -y jenkins
#RUN yum clean all

##### download version 1.596-1.1
RUN wget -q -O /tmp/jenkins.rpm 'http://pkg.jenkins-ci.org/redhat/jenkins-1.596-1.1.noarch.rpm'
RUN rpm -ivh /tmp/jenkins.rpm

EXPOSE 8080 22

VOLUME ["/var/lib/jenkins", "/var/log/jenkins"]

# Kicking in
ENTRYPOINT service jenkins start; sleep 5; tail -f /var/log/jenkins/jenkins.log
