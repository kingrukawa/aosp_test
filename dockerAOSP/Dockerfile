FROM ubuntu:16.04

MAINTAINER kingrukawa <276719644@qq.com>

# 163国内源
COPY 163.list /etc/apt/sources.list

# 软件
RUN dpkg --add-architecture i386 && \
apt-get update && \
apt-get install -y apt-utils && \
apt-get install -y wget && \
apt-get install -y libncurses5:i386 libstdc++6:i386 zlib1g:i386 lib32z1 lib32stdc++6 && \
apt-get clean

# JDK下载
RUN wget --no-check-certificate -c --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u66-b17/jdk-8u66-linux-x64.tar.gz

RUN tar -xzf jdk-8u66-linux-x64.tar.gz -C /usr/local && \
rm jdk-8u66-linux-x64.tar.gz

# 环境变量
ENV JAVA8_HOME /usr/local/jdk1.8.0_66
ENV JAVA_HOME /usr/local/jdk1.8.0_66
ENV PATH $PATH:$JAVA_HOME/bin

# android SDK
RUN wget http://dl.google.com/android/android-sdk_r24.4.1-linux.tgz && \
tar -xzf android-sdk_r24.4.1-linux.tgz -C /usr/local && \
rm android-sdk_r24.4.1-linux.tgz

# 配置 Android SDK 环境变量
ENV ANDROID_HOME /usr/local/android-sdk-linux
ENV PATH $PATH:$ANDROID_HOME/tools
ENV PATH $PATH:$ANDROID_HOME/platform-tools
ENV PATH $PATH:$ANDROID_HOME/build-tools

RUN echo yes | android update sdk --no-ui --all --filter platform-tools             && \
    echo yes | android update sdk --no-ui --all --filter build-tools-23.0.3	        && \
    echo yes | android update sdk --no-ui --all --filter build-tools-23.0.3	        && \
    echo yes | android update sdk --no-ui --all --filter android-23                 && \
    echo yes | android update sdk --no-ui --all --filter android-22                 && \
    echo yes | android update sdk --no-ui --all --filter extra-android-m2repository && \
    echo yes | android update sdk --no-ui --all --filter extra-android-support

# gradle
COPY gradle-2.14.1-all /usr/local/

ENV GRADLE_HOME /usr/local/gradle-2.14.1-all
ENV PATH $PATH:$GRADLE_HOME/bin

# 挂载文件目录（持久化文件，缓存 etc）
VOLUME ["/aospCache"]

# gradle 缓存设置
# RUN mkdir /aospCache/.gradle
ENV GRADLE_USER_HOME /home/aospCache/.gradle

# WORKDIR /home/demo/MyApplication
# RUN gradle clean
