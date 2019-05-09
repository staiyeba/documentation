.. _Macos guide:

MacOS Guide
===========

To start building on MacOS make sure to have a working installation of `brew <https://brew.sh/>`__ to be able to install all dependencies.

Dependencies
------------

For building the kernel you will need:

* `C/C++ package manager <https://docs.conan.io/en/latest/installation.html>`__ (Conan 1.13.1 or newer)
* cmake, make, nasm
* clang (Prebuilt packages are available for clang 6.0)

To boot VMs locally you will also need:

* qemu
* python3
* python packages: psutil, jsonschema

Once you have `homebrew <https://brew.sh/>`__ you can use our ``brew tap`` to install the dependencies as follows.

::

    $ brew tap includeos/includeos
    $ brew install includeos

Checkout our `homebrew formula for IncludeOS <https://github.com/includeos/homebrew-includeos>`__


**Getting Conan remotes and profiles**

We have set up a repository that will configure your local conan to use our build profiles and remote repositories.

.. warning::
  This overwrites any existing conan configuration.
  Thus you should set your ``CONAN_USER_HOME`` to create a separate conan home folder for testing.

::

    $ conan config install https://github.com/includeos/conan_config.git

If you prefer to set up conan manually the full configuration can be found in the `conan_config <https://github.com/includeos/conan_config.git>`__ repository.
