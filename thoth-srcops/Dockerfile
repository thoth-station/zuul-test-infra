FROM registry.access.redhat.com/ubi8-minimal:8.4-200

ENV SUMMARY="Thoth's SrcOps tools." \
    DESCRIPTION="Thoth's SrcOps tools." \
    GITHUB_CLI_VERSION="1.10.3"

LABEL summary="$SUMMARY" \
    description="$DESCRIPTION" \
    io.k8s.description="$DESCRIPTION" \
    io.k8s.display-name="Thoth SrcOps Tools" \
    io.openshift.tags="srcops,gh,github" \
    name="thoth-station/thoth-srcops"

RUN microdnf install --nodocs git-core && \ 
    rpm -i --nodeps --excludedocs https://github.com/cli/cli/releases/download/v1.10.3/gh_1.10.3_linux_amd64.rpm && \
    microdnf clean all
