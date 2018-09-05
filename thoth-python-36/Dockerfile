FROM registry.fedoraproject.org/fedora:28

ENV PYTHON_VERSION="3.6" \
    SUMMARY="Thoth's toolchain for testing Python $PYTHON_VERSION applications" \
    DESCRIPTION="Thoth's toolchain for testing Python $PYTHON_VERSION applications." \
    LANG="en_US.UTF-8"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="python,python36" \
      name="thoth-station/python-36" \
      version="0.1.4" \
      release="2" \
      usage="This is not a S2I builder image!" \
      maintainer="Christoph Görn <goern@redhat.com>"

RUN dnf update -y --setopt=tsflags=nodocs && \
    dnf install -y --setopt=tsflags=nodocs which python3-pip git && \
    dnf clean all && \
    pip3 install pipenv

COPY ./ /tmp/src/thoth-python-36-centos7
RUN pushd /tmp/src/thoth-python-36-centos7 && \
    pipenv lock -r > requirements.txt && \
    pip3 install -r requirements.txt && \
    mkdir -p /opt/app-root && \
    chmod 777 /opt/app-root && \
    chown 1042 /opt/app-root && \
    rm -rf /tmp/src

USER 1042

WORKDIR /opt/app-root
