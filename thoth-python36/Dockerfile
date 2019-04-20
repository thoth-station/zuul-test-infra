FROM registry.fedoraproject.org/fedora:28

ENV PYTHON_VERSION="3.6.8" \
    SUMMARY="Thoth's toolchain for Python ${PYTHON_VERSION} applications" \
    DESCRIPTION="Thoth's toolchain for Python ${PYTHON_VERSION} applications. This toolchain is based on Fedora 28. It includes the latest pipenv." \
    LANG="en_US.UTF-8" \
    USERID=1042 \
    HOME="/opt/app-root" \
    LC_ALL="en_US.UTF-8" \
    LANG="en_US.UTF-8" \
    PIP_NO_CACHE_DIR="off" \
    PATH="/opt/app-root/.local/bin:/opt/app-root/bin:$PATH" \
    SHELL="/usr/bin/bash"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="python,python36" \
      name="thoth-station/thoth-python36" \
      vendor="AICoE at the Office of the CTO, Red Hat Inc." \
      version="0.5.0" \
      release="0" \
      usage="This is not a S2I builder image!" \
      maintainer="Christoph Görn <goern@redhat.com>"

WORKDIR ${HOME}

RUN INSTALL_PKGS="gd-devel openssl-devel zlib-devel libcurl-devel libxml2-devel libxslt-devel \
    make autoconf automake bzip2 gcc-c++ patch gdb procps-ng unzip wget which git" && \
    dnf install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    dnf update -y --setopt=tsflags=nodocs && \
    dnf clean all -y && \
    pip3 install pipenv

RUN useradd -u ${USERID} -r -g 0 -d ${HOME} -s /sbin/nologin -c "Default Application User" default && \
    mkdir -p ${HOME}/.pki/nssdb ${HOME}/src/ ${HOME}/.local/ ${HOME}/.cache/ && \
    chown -R ${USERID}:0 ${HOME} && \
    chmod 777 -R ${HOME}/src/ ${HOME} ${HOME}/.cache/ ${HOME}/.local/

USER ${USERID}
