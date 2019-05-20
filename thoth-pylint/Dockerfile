FROM quay.io/aicoe/thoth-python36:fedora28

ENV SUMMARY="Thoth's toolchain for Pylint." \
    DESCRIPTION="Thoth's toolchain for Pylint."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-fedora28 Pylint" \
      io.openshift.tags="python,python36,pylint" \
      name="thoth-station/thoth-pylint:fedora28"

USER 0
COPY ./ /tmp/src-thoth-pylint
RUN DEINSTALL_PKGS="gd-devel openssl-devel zlib-devel libcurl-devel libxml2-devel libxslt-devel \
    make autoconf automake bzip2 gcc-c++ patch gdb procps-ng unzip wget" && \
    chmod 777 -R /tmp/src-thoth-pylint && \
    pushd /tmp/src-thoth-pylint && \
    cp pylintrc /etc/pylintrc && \
    chmod 644 /etc/pylintrc && \
    chown 0:0 /etc/pylintrc && \
    pip3 install --requirement requirements.txt && \
    dnf remove -y $DEINSTALL_PKGS

USER ${USERID}