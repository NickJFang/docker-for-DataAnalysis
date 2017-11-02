#
# Xgboost Dockerfile from
#
# https://github.com/dockerfile/java
# https:/https://github.com/NickJFang/docker-for-DataAnalysis
#
# Using https://github.com/phusion/baseimage-docker as a base image

# Pull base image.
FROM phusion/oracle-java:8

# Install git.
RUN \
  apt-get update && \
  apt-get install -y git
  

# install prerequisites enviroment: Maven 3+, and CMake 3.2+ f
RUN \
  apt-get install -y cmake && \
  apt-get install -y maven
  

# install xgboost
RUN \
  mkdir /home/app && \
  git clone https://github.com/dmlc/xgboost.git && \
  cd xgboost && \
  git submodule update --init --recursive


RUN \
  rm -rf /etc/service/sshd /etc/my_init.d/00_regen_ssh_host_keys.sh

# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Define default command.
CMD ["/sbin/my_init", "/bin/bash"]
