FROM quay.io/aicoe/thoth-python36:latest

ENV SUMMARY="Thoth's toolchain for pytest." \
    DESCRIPTION="Thoth's toolchain for pytest."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6 pytest" \
      io.openshift.tags="python,python36,pytest" \
      name="thoth-station/thoth-pytest"

USER 0
COPY ./ /tmp/src-thoth-pytest
RUN INSTALL_PKGS="gd-devel openssl-devel zlib-devel libcurl-devel libxml2-devel libxslt-devel \
    make autoconf automake bzip2 gcc-c++ patch gdb procps-ng unzip wget which git pipenv" && \
    chmod 777 -R /tmp/src-thoth-pytest && \
    pushd /tmp/src-thoth-pytest && \
    pip3 install --requirement requirements.txt && \
    dnf remove -y $INSTALL_PKGS

USER ${USERID}
