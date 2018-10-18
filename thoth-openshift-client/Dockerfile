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
RUN dnf install -y --setopt=tsflags=nodocs origin iputils curl

USER ${USERID}