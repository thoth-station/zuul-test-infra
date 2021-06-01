ARG OPF_GO_BASE=quay.io/fedora/fedora:34-x86_64

FROM ${OPF_GO_BASE} as gobuild

    # We're installing from sources, which results in a lot of cached code
    # we don't need in the final image. We use a multistage build so that
    # we can copy over the binaries in a subsequent stage and discard the
    # sources.

    ARG GOLANGCI_LINT_VERSION=1.40.1
    ARG REVIVE_VERSION=v1.0.6
    ARG STATICCHECK_VERSION=2020.2.4
    ARG INEFFASSIGN_VERSION=2e10b26
    ARG ERRCHECK_VERSION=v1.6.0
    ARG GHCLI_VERSION=1.10.3

    ENV GOPATH=/opt/app-root \
        PATH=/opt/app-root/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

    WORKDIR /opt/app-root/src

    RUN dnf -y install \
        golang \
        git

    RUN go install github.com/mgechev/revive@${REVIVE_VERSION}
    RUN go install honnef.co/go/tools/cmd/staticcheck@${STATICCHECK_VERSION}
    RUN go install github.com/gordonklaus/ineffassign@${INEFFASSIGN_VERSION}
    RUN go install github.com/kisielk/errcheck@${ERRCHECK_VERSION}

    RUN curl -L -o /tmp/golangci-lint.tar.gz \
        https://github.com/golangci/golangci-lint/releases/download/v${GOLANGCI_LINT_VERSION}/golangci-lint-${GOLANGCI_LINT_VERSION}-linux-amd64.tar.gz
    RUN tar -C /tmp -xv --strip-components=1 -f /tmp/golangci-lint.tar.gz && \
        cp /tmp/golangci-lint /opt/app-root/bin/

    RUN curl -L -o /tmp/ghcli.tar.gz https://github.com/cli/cli/releases/download/v${GHCLI_VERSION}/gh_${GHCLI_VERSION}_linux_amd64.tar.gz
    RUN tar -C /tmp -xv --strip-components=1 -f /tmp/ghcli.tar.gz && \
        cp /tmp/bin/gh /opt/app-root/bin/

FROM quay.io/thoth-station/s2i-thoth-f34-py39:latest

    ENV SUMMARY="Thoth's toolchain for running pre-commit hooks." \
        DESCRIPTION="Thoth's toolchain for running pre-commit hooks."

    LABEL summary="$SUMMARY" \
        description="$DESCRIPTION" \
        io.k8s.description="$DESCRIPTION" \
        io.k8s.display-name="Thoth Pre-Commit (python 3.9, go 1.16)" \
        io.openshift.tags="pre-commit" \
        name="thoth-station/thoth-pre-commit:ubi8"

    USER 0

    COPY --from=gobuild /opt/app-root/bin /opt/app-root/bin

    RUN dnf -y install \
        golang \
        git \
        && \
        dnf clean all

    COPY requirements.txt /tmp/src-thoth-precommit/requirements.txt

    RUN  \
      pip3 install --upgrade pip && \
      pip3 install --requirement /tmp/src-thoth-precommit/requirements.txt

    USER ${USERID}
