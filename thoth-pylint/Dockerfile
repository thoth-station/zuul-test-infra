FROM thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for Pylint." \
    DESCRIPTION="Thoth's toolchain for Pylint." \
    XDG_CACHE_HOME="/tmp"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 Pylint" \
      io.openshift.tags="python,python36,pylint" \
      name="thoth-station/thoth-pylint"

USER 0
COPY ./ /tmp/src-thoth-pylint
RUN chmod 777 -R /tmp/src-thoth-pylint && \
    pushd /tmp/src-thoth-pylint && \
    cp pylintrc /etc/pylintrc && \
    chmod 644 /etc/pylintrc && \
    chown 0:0 /etc/pylintrc && \
    pip3 install --requirement requirements.txt

USER ${USERID}