FROM jenkins

MAINTAINER kingrukawa <276719644@qq.com>

USER root

COPY 163.list /etc/apt/sources.list

RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN apt-get update &&\
apt-get install -y wget curl libncurses5:i386 libstdc++6:i386 zlib1g:i386 lib32z1 lib32stdc++6 &&\
apt-get clean


