FROM quay.io/aicoe/thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for Black." \
    DESCRIPTION="Thoth's toolchain for Black."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 Black" \
      io.openshift.tags="python,python36,black" \
      name="thoth-station/thoth-black"

USER 0
COPY ./ /tmp/src-thoth-coala
RUN chmod 777 -R /tmp/src-thoth-coala && \
    pushd /tmp/src-thoth-coala && \
    pip3 install --requirement requirements.txt

USER ${USERID}
