# Thoth's Zuul Infrastructure Stuff - OUTDATED

## Python 3.6 Toolchain

This container image could be used by a human, or some CI like Jenkins or Zuul to run linters, and provers...

```shell
cd thoth-python36
buildah build-using-dockerfile --tag thoth-python-36:latest .
gopass show aicoe/thoth/quay.io/robot-users # get the credentials
sudo skopeo copy containers-storage:localhost/thoth-python-36:latest docker://quay.io/aicoe/thoth-python36:v0.5.0 --dest-creds aicoe+ptah:<password>

```

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

### Thoth usage

[Thoth's Zuul](https://managesf.thoth-station.ninja/zuul/t/local/status.html) is using this container image with the [thoth-coala job]().