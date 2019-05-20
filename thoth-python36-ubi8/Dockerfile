FROM registry.access.redhat.com/ubi8/python-36:1-24

ENV SUMMARY="Thoth's toolchain for Python ${PYTHON_VERSION} applications" \
    DESCRIPTION="Thoth's toolchain for Python ${PYTHON_VERSION} applications. This toolchain is based on Red Hat UBI8. It includes pipenv." \
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
      io.k8s.display-name="Thoth Python 3.6-ubi8" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="python,python36" \
      name="thoth-station/thoth-python36:ubi8" \
      vendor="AICoE at the Office of the CTO, Red Hat Inc." \
      version="0.7.0" \
      release="0" \
      maintainer="Christoph Görn <goern@redhat.com>"

WORKDIR ${HOME}

RUN yum install -y python2 && \
    pip3 install pipenv
