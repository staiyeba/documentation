.. _Getting started:

Getting started with IncludeOS
==============================

Let's get started by cloning the repository and building IncludeOS.

Cloning the IncludeOS repository
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::
    $ git clone https://github.com/hioa-cs/IncludeOS
    $ cd IncludeOS


Dependencies
~~~~~~~~~~~~

To build a minimal IncludeOS the following dependencies are required at the moment.

- Cmake, make, nasm
- Clang or GCC
- `Conan <https://github.com/conan-io/conan>`__

> For more specific installation instructions for mac or linux checkout the linux guide or mac os guide.

To boot VMs locally you will also need:

* qemu
* python3
* python packages: psutil, jsonschema

> For Mac OS ensure that you have a working installation of [brew](https://brew.sh/) to be able to install all dependencies. To get help with your conan setup follow the instruction at :ref:`Conan Configuration <Conan configs>`

Hello World with IncludeOS
~~~~~~~~~~~~~~~~~~~~~~~~~~

Let's get started with getting our traditional hello World with IncludeOS.
You don't need to install IncludeOS to run a service, so just clone the service
repository.

```
    $ git clone https://github.com/includeos/hello_world
    $ cd hello_world
```
You will need to ensure you have our conan package remote and profiles in place
to build/run the service. The [IncludeOS](https://www.includeos.org/) conan recipes are developed with [Conan version 1.13.1](https://github.com/conan-io/conan/releases/tag/1.13.1) or newer.

```
    $ conan config install https://github.com/includeos/conan_config
```
**Selecting an appropriate [conan profile](https://docs.conan.io/en/latest/reference/profiles.html)**

First of running `conan profile list` will show the profiles installed.
- Linux users can typically use `clang-6.0-linux-x86_64`
- MacOS users can use `clang-6.0-macos-x86_64`. You can also make your own.

The following steps let you build and boot the IncludeOS hello world example.

::
    bash
    $ git clone https://github.com/includeos/hello_world.git
    $ mkdir your_build_dir && cd "$_"
    $ conan install ../hello_world -pr <your_conan_profile>
    $ source activate.sh
    $ cmake ../hello_world
    $ cmake --build .
    $ boot hello

For more advanced examples see the [examples repo](https://github.com/includeos/demo-examples). Once you're done `$ source deactivate.sh` will reset the environment to its previous state.


.. toctree::
   :maxdepth: 1
   :caption: To learn more about building IncludeOS kernel and it's dependencies visit our guide pages.

   Linux-guide
   Macos-guide
   Howto-Kernel-dev
   Howto-Service-dev
