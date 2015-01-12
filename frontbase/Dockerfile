#
# TreasureBoat.org
# by daveeed
#
# Frontbase 5.2.14 on CentOS 6.6
#
# build : docker build -t treasureboat/frontbase:0.1 .
# run : docker run -d -P --name tbFB5 treasureboat/frontbase:0.1

FROM treasureboat/java:latest
MAINTAINER treasureboat <programmingosx@mac.com>

# download FrontBase
RUN wget -q -O /tmp/FrontBase-5-2-14.rpm 'https://dl.dropboxusercontent.com/u/1548210/TB/Docker/FrontBase-5.2.14-CentOS-5.4-x86_64.rpm'

# install FrontBase
RUN rpm -i /tmp/FrontBase-5-2-14.rpm
RUN rm -f /tmp/FrontBase-5-2-14.rpm

# start FrontBase
RUN /usr/local/FrontBase/bin/FBExec &

# check if it is running
RUN touch /tmp/isFBRunning.txt
RUN ps axc | grep FBExec > /tmp/isFBRunning.txt
RUN cat /tmp/isFBRunning.txt
# RUN rm -f /tmp/isFBRunning.txt

