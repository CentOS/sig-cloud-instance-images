FROM scratch

MAINTAINER cncapf <cplasf1105@gmail.com>

ADD centos-7.4.1708-docker.tar.xz /

LABEL name="CentOS Base Image" \
    vendor="CentOS" \
    license="GPLv2" \
    build-date="20190211"

# add aliyun repository
COPY CentOS-Base.repo /etc/yum.repos.d/

# update and clean all
RUN yum -y update \
    && yum clean all

# set timezone
ENV TZ=Asia/Shanghai

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

CMD ["/bin/bash"]
