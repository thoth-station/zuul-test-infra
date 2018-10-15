FROM thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for Coala linting." \
    DESCRIPTION="Thoth's toolchain for Coala linting." \
    XDG_DATA_HOME="/tmp"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 Coala" \
      io.openshift.tags="python,python36,coala" \
      name="thoth-station/python-coala" \
      version="0.1.0" \
      release="0"

COPY ./ /tmp/src/thoth-python-36
RUN pushd /tmp/src/thoth-python-36 && \
    pipenv lock -r > requirements.txt && \
    pip3 install -r requirements.txt && \
    rm -rf /tmp/src
