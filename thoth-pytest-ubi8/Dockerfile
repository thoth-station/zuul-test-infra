FROM quay.io/aicoe/thoth-python36:v0.8.0-ubi8

ENV SUMMARY="Thoth's toolchain for pytest." \
    DESCRIPTION="Thoth's toolchain for pytest."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-ubi8 pytest" \
      io.openshift.tags="python,python36,pytest" \
      name="thoth-station/thoth-pytest:ubi8"

USER 0
COPY ./ /tmp/src-thoth-pytest
RUN yum install -y python2 && \
    pip3 install --requirement /tmp/src-thoth-pytest/requirements.txt

USER ${USERID}
