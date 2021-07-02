FROM registry.access.redhat.com/ubi8:latest

LABEL maintainer="The CentOS Project"

LABEL com.redhat.component="centos-stream-container" \
      name="centos-stream" \
      version="8"

LABEL com.redhat.license_terms="https://centos.org/legal/licensing-policy/"

LABEL summary="Provides a CentOS Stream container based on the Red Hat Universal Base Image"
LABEL description="CentOS Stream is a continuously delivered distro that tracks just ahead of Red Hat Enterprise Linux development. This image takes the Red Hat UBI and layers on content from CentOS Stream"
LABEL io.k8s.display-name="CentOS Stream 8"
LABEL io.openshift.expose-services=""
LABEL io.openshift.tags="base centos centos-stream"

RUN dnf download --repofrompath=centos,http://mirror.centos.org/centos/8-stream/BaseOS/x86_64/os/ --disablerepo=* --enablerepo=centos centos-stream-release centos-stream-repos centos-gpg-keys
RUN rpm -ivh --nodeps --replacefiles *.rpm && rm *.rpm \
    && rpm -e redhat-release \
    && dnf --setopt=tsflags=nodocs --setopt=install_weak_deps=false -y distro-sync \
    && dnf remove -y subscription-manager dnf-plugin-subscription-manager\
    && dnf clean all \
    && rm -f /etc/yum.repos.d/ubi.repo
