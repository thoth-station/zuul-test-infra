# Thoth's Zuul Infrastructure Stuff

## Python 3.6 Toolchain

```shell
cd thoth-python-36-centos7
sudo buildah build-using-dockerfile --tag thoth-python-36-centos7 .
gopass show aicoe/thoth/quay.io/robot-users
sudo skopeo copy containers-storage:ba678799b9c51858d39cf3fea246d73c77416d2ca353955d04d7a1dacd8846a3 docker://quay.io/aicoe/thoth-python-36-centos7:v0.1.0 --dest-creds aicoe+ptah:<password>

```