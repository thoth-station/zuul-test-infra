FROM quay.io/aicoe/thoth-python36:v0.8.0-ubi8

ENV SUMMARY="Thoth's toolchain for mypy." \
    DESCRIPTION="Thoth's toolchain for mypy."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-ubi8 mypy" \
      io.openshift.tags="python,python36,mypy" \
      name="thoth-station/thoth-mypy:ubi8"

USER 0
COPY ./ /tmp/src-thoth-mypy
RUN pip3 install --requirement /tmp/src-thoth-mypy/requirements.txt

USER ${USERID}