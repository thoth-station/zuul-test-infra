FROM quay.io/thoth-station/s2i-thoth-f31-py37:v0.11.3

ENV SUMMARY="Thoth's toolchain for pytest." \
    DESCRIPTION="Thoth's toolchain for pytest."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.7-f31 pytest" \
      io.openshift.tags="python,python37,pytest" \
      name="thoth-station/thoth-pytest:fedora31" \
      version="0.10.0"

USER 0
COPY ./ /tmp/src-thoth-pytest
RUN yum install -y python2 && \
    /usr/bin/pip3 install --requirement /tmp/src-thoth-pytest/requirements.txt

USER ${USERID}
