.. _Building Docker Images:

Building Docker images
======================

This allows anyone to build `IncludeOS <https://github.com/hioa-cs/IncludeOS/>`_
unikernels on docker without having to install the development environment locally on the machine.

Build options
~~~~~~~~~~~~~

When building the docker image there are a few options available:

+-----------------------+--------------------------------------------+
|       **Action**      |                  **Command**               |
|-----------------------|--------------------------------------------|
| Specify build version | --build-arg TAG=<git tag/version to build> |
|-----------------------|--------------------------------------------|
|   Service to build    | --target=<build/grubify/webserver>         |
|-----------------------|--------------------------------------------|
|      Custom Tag       |  --build-arg TAG=<custom-tag>              |
+-----------------------+--------------------------------------------+

Docker tag structure
~~~~~~~~~~~~~~~~~~~~

The docker tags in use for these images are:

::

<org>/<service>:<IncludeOS_Tag>.<Dockerfile version> includeos/build:v0.12.0-rc.3.1

For every change made to the Dockerfile the corresponding tag is incremented.

Building services
~~~~~~~~~~~~~~~~~

As specified above there are a number of options for building IncludeOS.
All of the options are optional.


Building services with IncludeOS build tags
-------------------------------------------

To build with IncludeOS internal build tags, it can be done as follows:

::

$ docker build --build-arg TAG=v0.12.0-rc.4 --target=build -t includeos/build:v0.12.0-rc.4.01 .

::

$ cd <my-super-cool-service>

::

$ docker run --rm -v $PWD:/service includeos/build:v0.12.0-rc.4.01


Building services with Users own custom tags
--------------------------------------------

The tagging works in order of precedence as;

  - Checks for custom tag, if specified in `$TAG` by user during build then remove present tag and replace with new tag

  - If custom tag is not provided during build, the tag found in `git describe --tags` is used. The tag found can either be a default tag specified by IncludeOS

  - Or it could also be a tag assigned by a user with `git tag $TAG`


The custom tag can be assigned during build as follows:

::

$ docker build --build-arg TAG=myKoolTag -t <username>/includeos-build:v0.12.0-rc.4.01 .

::

$ docker run --rm -v $PWD:/service <username>/includeos-build:v0.12.0-rc.4.01



Example: Building our Service - Starbase
----------------------------------------

::

$ cd IncludeOS

::

$ docker build --build-arg TAG=buildStarbase -t includeos/dev:v0.12.0-rc-4 .

::

$ cd lib/uplink/starbase/

::

$ docker run --rm -v $PWD:/service includeos/dev:v0.12.0-rc-4


**Note:**  Remember to remove (if present) the build folder present in the service (starbase) directory with:

::

$ rm -rf build

and then run with the above docker run command.
