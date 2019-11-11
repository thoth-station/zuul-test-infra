# Changelog for Thoth's Python tool chain

## [0.9.6] - 2019-Nov-11 - goern - the Alaaf release

### Changes

The whole toolchain has been rebased on the current RHEL8.1 based UBI8 container image, tagged [1-62](https://access.redhat.com/containers/?architecture=#/registry.access.redhat.com/ubi8/python-36/images/1-62). This updated came in via [Thoth's S2I](https://quay.io/repository/thoth-station/s2i-thoth-ubi8-py36?tab=info).

All tools have been updated to their current version, this does include `black`, `coala`, `mypy`, `pylint` and `pytest`.

Thoth's Zuul infrastructure for the [AICoE](https://github.com/AICoE) and [Thoth-Station](https://github.com/thoth-station) is using these released now!

Please report any issues to https://github.com/thoth-station/zuul-infra/issues

## [0.9.0] - 2019-Aug-27 - goern

### Added

Added a thoth-mypy container image to be used by Zuul.

### Changes

UBI8 image now use [Thoth's S2I](https://quay.io/repository/thoth-station/s2i-thoth-ubi8-py36?tab=info) as a base image.

## [0.7.0] - 2019-Jun-28 - goern

### Added

This release is basing the Thoth Python tool chain on RHEL UBI8 images and Python 3.6. To run [Coala](https://coala.io/#/home?lang=Python) use something like `podman run --rm -ti -v $(pwd):/opt/app-root/src:Z quay.io/thoth-station/thoth-coala:v0.7.0-ubi8`.

### Changed

With this release we are no longer providing up to date builds based on Fedora. The last version was based on Fedora 28.
