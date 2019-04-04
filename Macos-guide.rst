.. _Macos guide:

Building on MacOS
=================

To start building on MacOS make sure to have a working installation of [brew](https://brew.sh/) to be able to install all dependencies.

Building the kernel on MacOS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To start building the kernel on MacOS start by installing the dependencies.

Dependencies
------------

- Cmake
- Conan

#### macOS
If you have [homebrew](https://brew.sh/) you can use our `brew tap` to install the dependencies.

```text
$ brew tap includeos/includeos
$ brew install includeos
$ conan config install https://github.com/includeos/conan_config.git
```
