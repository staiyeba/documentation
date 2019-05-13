.. _in depth install:

Getting started with IncludeOS
==============================

IncludeOS is an open source project and can be found on `Github <https://github.com/includeos/IncludeOS>`__ .
Whether you are a kernel or a service developer using MacOS or Linux, below is a list of sections that will guide you through the process of building and starting an IncludeOS service.

.. toctree::
   :maxdepth: 1

   Linux-guide
   Macos-guide
   Howto-Kernel-dev
   Howto-Service-dev

Hello World with IncludeOS
~~~~~~~~~~~~~~~~~~~~~~~~~~

To start of we welcome you to trying a simple traditional Hello World with IncludeOS.
You don't need to install IncludeOS to run a service, so just clone the service
repository.

::

    $ git clone https://github.com/includeos/hello_world
    $ cd hello_world

Dependencies
------------

To build the service you will need:

* Cmake, make, nasm
* Clang or GCC
* `Conan <https://github.com/conan-io/conan>`__

To boot VMs locally you will need:

* qemu
* python3
* python packages: psutil, jsonschema

The `IncludeOS <https://www.includeos.org/>`__ conan packages are available on
bintray. Therefore you will need to add the remote to your list. Conan requires
the use of a profile during building a package, which can also be installed using
the command below.

::

    $ conan config install https://github.com/includeos/conan_config

.. note::
   For Mac OS ensure that you have a working installation of `brew <https://brew.sh>`__ to be able to install all dependencies. For more specific installation instructions for mac or linux checkout the linux guide or mac os guide listed above. To get help with your conan setup follow the instruction at :ref:`Conan Configuration <Conan configs>`.

Running ``conan profile list`` will show the profiles installed.
- Linux users can typically use ``clang-6.0-linux-x86_64``
- MacOS users can use ``clang-6.0-macos-x86_64``.
You can also develop your own profiles.

The following steps let you build and boot the IncludeOS hello world example.

::

    $ git clone https://github.com/includeos/hello_world.git
    $ mkdir your_build_dir && cd "$_"
    $ conan install ../hello_world -pr <your_conan_profile>
    $ source activate.sh
    $ cmake ../hello_world
    $ cmake --build .
    $ boot hello

.. warning::
    Once you're done ``$ source deactivate.sh`` will reset your environment to
    its previous state.

For more advanced examples see the `examples repo <https://github.com/includeos/demo-examples>`__.
