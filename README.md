# helics-buildenv
[![Docker Image CI Status](https://github.com/GMLC-TDC/helics-buildenv/workflows/Docker%20Image%20CI/badge.svg)](https://github.com/GMLC-TDC/helics-buildenv/actions)

**helics-buildenv** contains files related to setting up build environments for HELICS repositories. Right now it consists of Dockerfiles for generating images used in builds. The container images are pushed to [helics/buildenv](https://hub.docker.com/r/helics/buildenv) on Docker Hub.

## Dockerfiles
Each Dockerfile has its own directory that contains all the scripts needed to build it. A GitHub Actions workflow is setup to build and push updated Docker images to Docker Hub. To manually build a Dockerfile, go to its subfolder and then run `docker build . --tag "helics/buildenv:<tag>"`.

- *builder*: Creates a general-purpose Ubuntu builder image with the default ZMQ, Boost, CMake, git, and g++ packages.
- *ci-builders*: Creates parameterized Ubuntu CI images with selectable compiler, Boost, and MPI versions. Arguments taken are `COMPILER` (for example `gcc-4.9`), `MPI_VARIANT`, `MPICH_VERSION`, and `BOOST_VERSION`.
- *clang-format*: An Alpine image with the tools needed to run clang-format installed.
- *interface-gen*: Creates a Fedora 31 image with SWIG 4.0.1 and SWIG Matlab (https://github.com/jaeandersson/swig) installed.
- *octave*: Provides Ubuntu-based Octave images, including newer `octave-8` variants.
- *sanitizers*: Provides Clang sanitizer images built from the matching HELICS Clang builder images.
- Recent builder images include Ubuntu 24.04 and Ubuntu 26.04 variants for newer Clang and GCC toolchains, along with pinned utility images such as `cpplint` and `cppcheck2`.

## Release
helics-buildenv is distributed under the terms of the BSD-3 clause license. All new
contributions must be made under this license. [LICENSE](LICENSE)

SPDX-License-Identifier: BSD-3-Clause
