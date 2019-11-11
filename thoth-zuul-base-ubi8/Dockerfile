FROM quay.io/thoth-station/s2i-thoth-ubi8-py36:v0.4.0

ENV SUMMARY="Thoth's Zuul toolchain "

LABEL summary="$SUMMARY" \
      description="$SUMMARY" \
      io.k8s.description="$SUMMARY" \
      version="0.9.4" \
      release="0"

USER 0

RUN INSTALL_PKGS="python2" && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS

USER ${USERID}
