FROM quay.io/thoth-station/thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for Coala linting." \
    DESCRIPTION="Thoth's toolchain for Coala linting."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 Coala" \
      io.openshift.tags="python,python36,coala" \
      name="thoth-station/thoth-coala"

USER 0
COPY ./ /tmp/src-thoth-coala
RUN chmod 777 -R /tmp/src-thoth-coala && \
    pushd /tmp/src-thoth-coala && \
    pip3 install --requirement requirements.txt

USER ${USERID}
