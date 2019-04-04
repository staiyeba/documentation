.. _Linux guide:

Linux Guide
===========

We are currently developing and testing on ``Ubuntu-18.04``. To get started with
building on Linux, install the following dependencies.


Dependencies
------------

For building the kernel you will need:

* `C/C++ package manager <https://docs.conan.io/en/latest/installation.html>`__ (Conan 1.13.1 or newer)
* cmake, make, nasm
* clang, or alternatively gcc on linux. Prebuilt packages are available for clang 6.0 and gcc 7.3.

To boot VMs locally you will also need:

* qemu
* python3
* python packages: psutil, jsonschema

You can use the recipe below to get all the dependencies in place.

::

    $ apt-get install python3-pip python3-dev git cmake clang-6.0 gcc nasm make qemu
    $ pip3 install setuptools wheel conan psutil jsonschema


*Getting Conan remotes and profiles*

We have set up a repository that will configure your local conan to use our build profiles and remote repositories.

.. warning::
  This overwrites any existing conan configuration.
  Thus you should set your ``CONAN_USER_HOME`` to create a separate conan home folder for testing.

::

    $ conan config install https://github.com/includeos/conan_config.git

If you prefer to set up conan manually the full configuration can be found in the [conan_config](https://github.com/includeos/conan_config.git)-repository.

.. _Build linux:

Building the kernel on Linux
----------------------------

To build IncludeOS on Linux for Linux you can use the profile named
``clang-6.0-linux-x86_64`` or ``gcc-7.3.0-linux-x86_64`` :
