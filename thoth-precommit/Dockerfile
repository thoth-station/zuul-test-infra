FROM quay.io/thoth-station/s2i-thoth-ubi8-py38:v0.20.1

ENV SUMMARY="Thoth's toolchain for running pre-commit hooks." \
    DESCRIPTION="Thoth's toolchain for running pre-commit hooks."

LABEL summary="$SUMMARY" \
    description="$DESCRIPTION" \
    io.k8s.description="$DESCRIPTION" \
    io.k8s.display-name="Thoth Python 3.8-ubi8 Pre-Commit" \
    io.openshift.tags="python,python38,pre-commit" \
    name="thoth-station/thoth-pre-commit:ubi8" \
    version="0.12.2"

USER 0
COPY ./ /tmp/src-thoth-precommit
RUN  \
  pip install --upgrade pip &&\
  /usr/bin/python3 -m pip install --upgrade pip &&\
  /usr/bin/python3 -m pip install --requirement /tmp/src-thoth-precommit/requirements.txt

USER ${USERID}
