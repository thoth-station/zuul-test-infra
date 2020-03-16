FROM quay.io/aicoe/thoth-python36:fedora28

ENV SUMMARY="Thoth's toolchain for pytest." \
    DESCRIPTION="Thoth's toolchain for pytest."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-fedora28 pytest" \
      io.openshift.tags="python,python36,pytest" \
      name="thoth-station/thoth-pytest:fedora28"

USER 0
COPY ./ /tmp/src-thoth-pytest
RUN dnf install -y --setopt=tsflags=nodocs @development-tools python3-devel && \
    chmod 777 -R /tmp/src-thoth-pytest && \
    pushd /tmp/src-thoth-pytest && \
    /usr/bin/pip3 install --requirement requirements.txt

USER ${USERID}
