FROM registry.fedoraproject.org/fedora:28

ENV SUMMARY="Thoth's toolchain to operate OpenShift from within OpenShift." \
    DESCRIPTION="Thoth's toolchain to operate OpenShift from within OpenShift."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth OpenShift Client" \
      io.openshift.tags="thoth,openshift-client" \
      name="thoth-station/thoth-openshift-client"

USER 0
COPY ./ /tmp/src-thoth-coala
RUN dnf install -y --setopt=tsflags=nodocs origin iputils curl && \
    chmod 777 -R /tmp/src-thoth-coala && \
    pushd /tmp/src-thoth-coala && \
    pip3 install --requirement requirements.txt

USER ${USERID}