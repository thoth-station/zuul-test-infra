FROM quay.io/aicoe/thoth-python36:fedora28

ENV SUMMARY="Thoth's toolchain for Black." \
    DESCRIPTION="Thoth's toolchain for Black."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-fedora28 Black" \
      io.openshift.tags="python,python36,black" \
      name="thoth-station/thoth-black:fedora28"

USER 0
COPY ./ /tmp/src-thoth-black
RUN DEINSTALL_PKGS="gd-devel openssl-devel zlib-devel libcurl-devel libxml2-devel libxslt-devel \
    make autoconf automake bzip2 gcc-c++ patch gdb procps-ng unzip wget" && \
    chmod 777 -R /tmp/src-thoth-black && \
    pushd /tmp/src-thoth-black && \
    pip3 install --requirement requirements.txt && \
    dnf remove -y $DEINSTALL_PKGS

USER ${USERID}
