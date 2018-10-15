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

COPY ./ ${HOME}/src-thoth-pylint
RUN pushd ${HOME}/src-thoth-pylint && \
    pipenv install && \
    rm -rf ${HOME}/src-thoth-pylint
