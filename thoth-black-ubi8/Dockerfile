FROM quay.io/thoth-station/s2i-thoth-ubi8-py36:v0.12.4

ENV SUMMARY="Thoth's toolchain for Black." \
    DESCRIPTION="Thoth's toolchain for Black."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Thoth Python 3.6-ubi8 Black" \
      io.openshift.tags="python,python36,black" \
      name="thoth-station/thoth-black:ubi8" \
      version="0.10.3"

USER 0
COPY ./ /tmp/src-thoth-coala
RUN pip3 install --requirement /tmp/src-thoth-coala/requirements.txt

USER ${USERID}
