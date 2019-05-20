FROM quay.io/aicoe/thoth-python36:fedora28

ENV SUMMARY="Thoth's toolchain for Coala linting." \
    DESCRIPTION="Thoth's toolchain for Coala linting."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-fedora28 Coala" \
      io.openshift.tags="python,python36,coala" \
      name="thoth-station/thoth-coala:fedora28"

USER 0
COPY ./ /tmp/src-thoth-coala
RUN DEINSTALL_PKGS="gd-devel openssl-devel zlib-devel libcurl-devel libxml2-devel libxslt-devel \
    make autoconf automake bzip2 gcc-c++ patch gdb procps-ng unzip wget" && \
    chmod 777 -R /tmp/src-thoth-coala && \
    pushd /tmp/src-thoth-coala && \
    pip3 install --requirement requirements.txt && \
    dnf remove -y $DEINSTALL_PKGS

USER ${USERID}
