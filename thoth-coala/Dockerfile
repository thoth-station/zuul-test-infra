FROM thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for Coala linting." \
    DESCRIPTION="Thoth's toolchain for Coala linting." \
    XDG_DATA_HOME="/tmp"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 Coala" \
      io.openshift.tags="python,python36,coala" \
      name="thoth-station/thoth-coala" \
      version="0.3.0" \
      release="0"

USER 0
COPY ./ /tmp/src-thoth-coala
RUN chmod 777 -R /tmp/src-thoth-coala

USER ${USER}
RUN pushd /tmp/src-thoth-coala && \
    pip3 install --requirement requirements.txt --user
