FROM registry.centos.org/centos/python-36-centos7:latest 

ENV SUMMARY="Thoth's toolchain for testing Python $PYTHON_VERSION applications" \
    DESCRIPTION="Thoth's toolchain for testing Python $PYTHON_VERSION applications."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="python,python36,rh-python36" \
      name="thoth-station/thoth-python-36-centos7" \
      version="1" \
      usage="This is not a S2I builder image!" \
      maintainer="Christoph Görn <goern@redhat.com>"

USER 0

RUN pip install pipenv coala-bears pylint

USER 1001