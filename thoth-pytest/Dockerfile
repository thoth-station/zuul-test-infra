FROM thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for pytest." \
    DESCRIPTION="Thoth's toolchain for pytest." \
    XDG_CACHE_HOME="/tmp"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 pytest" \
      io.openshift.tags="python,python36,pytest" \
      name="thoth-station/thoth-pytest"

USER 0
COPY ./ /tmp/src-thoth-pytest
RUN chmod 777 -R /tmp/src-thoth-pytest && \
    pushd /tmp/src-thoth-pytest && \
    pip3 install --requirement requirements.txt

USER ${USERID}
