# naive approach to building a no-longer developed nodejs app for the purposes
# of making a better debugging experience when running docker-compose
FROM centos:centos7.6.1810

ENV container=docker

# Install all the needed repos
RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7 \
    && yum -y update \
    && yum -y install epel-release -y \
    && rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7

# install the required packages
RUN yum -y install npm supervisor

# configure nodejs/npm to be more verbose
RUN npm install --global debug --save
RUN export DEBUG='npm node'
RUN npm config set loglevel silly

# install sample software
RUN npm install --global geoserver

# download tests
# RUN yum -y install zip maven \
#    && curl -kvO https://repo.boundlessgeo.com/main/org/geoserver/geoserver/2.5.2/geoserver-2.5.2-tests.jar

# COPY files /

CMD ["init"]
