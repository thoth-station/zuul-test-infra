FROM thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for Pylint." \
    DESCRIPTION="Thoth's toolchain for Pylint."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 Coala" \
      io.openshift.tags="python,python36,coala" \
      name="thoth-station/python-coala" \
      version="0.1.0" \
      release="0"

COPY ./ ${HOME}/src-thoth-pylint

USER 0
RUN pushd ${HOME}/src-thoth-pylint && \
    cp pylintrc /etc/pylintrc && \
    chmod 644 /etc/pylintrc && \
    chown 0:0 /etc/pylintrc

USER ${USERID}
RUN pushd ${HOME}/src-thoth-pylint && \
    pipenv install && \
    rm -rf ${HOME}/src-thoth-pylint