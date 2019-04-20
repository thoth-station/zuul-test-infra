FROM quay.io/aicoe/thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for Pylint." \
    DESCRIPTION="Thoth's toolchain for Pylint."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 Pylint" \
      io.openshift.tags="python,python36,pylint" \
      name="thoth-station/thoth-pylint"

USER 0
COPY ./ /tmp/src-thoth-pylint
RUN INSTALL_PKGS="gd-devel openssl-devel zlib-devel libcurl-devel libxml2-devel libxslt-devel \
    make autoconf automake bzip2 gcc-c++ patch gdb procps-ng unzip wget which git pipenv" && \
    chmod 777 -R /tmp/src-thoth-pylint && \
    pushd /tmp/src-thoth-pylint && \
    cp pylintrc /etc/pylintrc && \
    chmod 644 /etc/pylintrc && \
    chown 0:0 /etc/pylintrc && \
    pip3 install --requirement requirements.txt && \
    dnf remove -y $INSTALL_PKGS

USER ${USERID}