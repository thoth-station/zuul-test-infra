FROM quay.io/thoth-station/s2i-thoth-ubi8-py36:v0.20.1

ENV SUMMARY="Thoth's toolchain for running pre-commit hooks." \
    DESCRIPTION="Thoth's toolchain for running pre-commit hooks."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-ubi8 Pre-Commit" \
      io.openshift.tags="python,python36,pre-commit" \
      name="thoth-station/thoth-pre-commit:ubi8"

USER 0
COPY ./ /tmp/src-thoth-precommit
RUN  \
  /usr/bin/pip3 install --upgrade pip &&\
  /usr/bin/pip3 install --requirement /tmp/src-thoth-precommit/requirements.txt

USER ${USERID}
