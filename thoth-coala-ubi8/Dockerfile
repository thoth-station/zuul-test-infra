FROM quay.io/thoth-station/s2i-thoth-ubi8-py36:v0.20.1

ENV SUMMARY="Thoth's toolchain for Coala linting." \
    DESCRIPTION="Thoth's toolchain for Coala linting."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-ubi8 Coala" \
      io.openshift.tags="python,python36,coala" \
      name="thoth-station/thoth-coala:ubi8" \
      version="0.12.1"

USER 0
COPY ./ /tmp/src-thoth-coala
COPY ./root/ /

RUN yum install -y python2 && \
    npm install -g remark-cli remark-lint && \
    /usr/bin/pip3 install --upgrade pip &&\
    /usr/bin/pip3 install --requirement /tmp/src-thoth-coala/requirements.txt

USER ${USERID}

ENTRYPOINT /usr/bin/thoth-coala
