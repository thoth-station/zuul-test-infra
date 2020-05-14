FROM quay.io/thoth-station/s2i-thoth-ubi8-python36:v0.11.3

ENV SUMMARY="Thoth's toolchain for running pre-commit hooks." \
    DESCRIPTION="Thoth's toolchain for running pre-commit hooks."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-fedora28 Pre-Commit" \
      io.openshift.tags="python,python36,pre-commit" \
      name="thoth-station/thoth-pre-commit:fedora28"

USER 0
COPY ./ /tmp/src-thoth-precommit
RUN /usr/bin/pip3 install --requirement /tmp/src-thoth-pylint/requirements.txt

USER ${USERID}
