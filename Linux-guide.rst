.. _Linux guide:

Building on Linux
=================

We are currently developing and testing on ``Ubuntu-18.04``. To get started with
building on Linux, install the dependencies.


For building IncludeOS services you will need:

* [The conan package manager](https://docs.conan.io/en/latest/installation.html) (1.13.1 or newer)
* cmake, make, nasm
* clang, or alternatively gcc on linux. Prebuilt packages are available for clang 6.0 and gcc 7.3.

To boot VMs locally you will also need:

* qemu
* python3
* python packages: psutil, jsonschema

The following command will configure conan to use our build profiles and remote repositories. (**Note:** this overwrites any existing conan configuration. Set `CONAN_USER_HOME` to create a separate conan home folder for testing.)

```text
$ conan config install https://github.com/includeos/conan_config.git
```
If you prefer to set up conan manually the full configuration can be found in the [conan_config](https://github.com/includeos/conan_config.git)-repository.

#### Ubuntu

```text
$ apt-get install python3-pip python3-dev git cmake clang-6.0 gcc nasm make qemu
$ pip3 install setuptools wheel conan psutil jsonschema
$ conan config install https://github.com/includeos/conan_config.git
