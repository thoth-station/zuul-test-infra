# Thoth's Ops Infrastructure

This project is used for maintaining the collection of thoth-ops infra images.

## Python 3.6 Toolchain

This container image could be used by a human, or some CI like Jenkins or Zuul to run linters, and provers...

```shell
cd thoth-python36
buildah build-using-dockerfile --tag thoth-python-36:latest .
gopass show aicoe/thoth/quay.io/robot-users # get the credentials
sudo skopeo copy containers-storage:localhost/thoth-python-36:latest docker://quay.io/aicoe/thoth-python36:v0.5.0 --dest-creds aicoe+ptah:<password>
```

### Thoth Ops Infra Images

Thoth-Ops Images          | Image Link/Status
------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
thoth-precommit-ubi8      | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-precommit/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-precommit)
thoth-precommit-ubi8-py38 | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-precommit/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-precommit-py38)
thoth-pytest-ubi8         | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-pytest/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-pytest)
thoth-pytest-ubi8-py38    | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-pytest-ubi8-py38/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-pytest-ubi8-py38)
thoth-pytest-f31-py37     | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-pytest-f31-py37/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-pytest-f31-py37)
thoth-mypy-ubi8           | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-mypi/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-mypi)
thoth-black-ubi8          | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-black/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-black)
thoth-coala-ubi8          | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-coala/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-coala)
thoth-pylint-ubi8         | [![Docker Repository on Quay](https://quay.io/repository/thoth-station/thoth-pylint/status "Docker Repository on Quay")](https://quay.io/repository/thoth-station/thoth-pylint)

### Test

Looking at the installed packages, as of v0.2.0 you should see:

```shell
$ podman run -ti --rm thoth-python36:latest pip --version
pip 9.0.3 from /usr/lib/python3.6/site-packages (python 3.6)
$ podman run -ti --rm thoth-python36:latest pipenv --version
pipenv, version 2018.7.1
$ podman run -ti --rm thoth-python36:latest coala --version
0.11.0
$ podman run -ti --rm thoth-python36:latest pylint --version
No config file found, using default configuration
pylint 1.9.3
```
