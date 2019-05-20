FROM quay.io/aicoe/thoth-python36:ubi8

ENV SUMMARY="Thoth's toolchain for Coala linting." \
    DESCRIPTION="Thoth's toolchain for Coala linting."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-ubi8 Coala" \
      io.openshift.tags="python,python36,coala" \
      name="thoth-station/thoth-coala:ubi8"

USER 0
COPY ./ /tmp/src-thoth-coala
RUN pip3 install --requirement /tmp/src-thoth-coala/requirements.txt

USER ${USERID}
