FROM registry.fedoraproject.org/fedora:28

ENV SUMMARY="Thoth's toolchain to operate OpenShift from within OpenShift." \
    DESCRIPTION="Thoth's toolchain to operate OpenShift from within OpenShift." \
    USERID=1042 \
    HOME="/opt/app-root"
    LANG="en_US.UTF-8" \
    LC_ALL="en_US.UTF-8" \
    LANG="en_US.UTF-8" \
    PIP_NO_CACHE_DIR="off" \
    PATH="/opt/app-root/.local/bin:/opt/app-root/bin:$PATH" \
    SHELL="/usr/bin/bash"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth OpenShift Client" \
      io.openshift.tags="thoth,openshift-client" \
      name="thoth-station/thoth-openshift-client"

WORKDIR ${HOME}

RUN useradd -u ${USERID} -r -g 0 -d ${HOME} -s /sbin/nologin -c "Default Application User" default && \
    mkdir -p ${HOME}/.pki/nssdb ${HOME}/src/ ${HOME}/.local/ ${HOME}/.cache/ ${HOME}.kube && \
    chown -R ${USERID}:0 ${HOME} && \
    chmod 777 -R ${HOME}/src/ ${HOME} ${HOME}/.cache/ ${HOME}/.local/ ${HOME}.kube

COPY ./ /tmp/src-thoth-ops

RUN INSTALL_PKGS="origin iputils curl which git" && \
    dnf install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    dnf update -y --setopt=tsflags=nodocs && \
    dnf clean all -y && \
    chmod 777 -R /tmp/src-thoth-ops && \
    pushd /tmp/src-thoth-ops && \
    pip3 install --requirement requirements.txt

USER ${USERID}
