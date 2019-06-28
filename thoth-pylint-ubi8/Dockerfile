FROM quay.io/aicoe/thoth-python36:v0.7.0-ubi8

ENV SUMMARY="Thoth's toolchain for Pylint." \
    DESCRIPTION="Thoth's toolchain for Pylint."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-ubi8 Pylint" \
      io.openshift.tags="python,python36,pylint" \
      name="thoth-station/thoth-pylint:ubi8"

USER 0
COPY ./ /tmp/src-thoth-pylint
RUN pip3 install --requirement /tmp/src-thoth-pylint/requirements.txt

USER ${USERID}