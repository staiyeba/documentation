.. _Conan package build:

Build Conan Packages for includeOS
==================================

Getting started building packages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Currently building works for ``clang-6`` and ``gcc-7.3.0`` compiler toolchain. It is expected that these are already installed in your system. However we hope to provide toolchains in the future.

Building Tools
--------------

Binutils is a tool and not an actual part of the final binary by having it added in the profile the binaries are always executable inside the conan environment.

The binutils tool must be built for the Host it's intended to run on. Therefore the binutils package is built using a special toolchain profile that doesn't have a requirement on binutils.

To build ``bintuils`` using our [conan recipes](https://github.com/includeos/conan):

- Clone the repository
- Do ``conan create`` as follows:

::
    $ conan create <binutils-conan-recipe-path>/binutils/2.31 -pr <yourprofilename>-toolchain includeos/test


Building Dependencies
---------------------

To build our other dependencies you may use the conan recipes we have in the repository.

Building musl
^^^^^^^^^^^^^

::
    $ conan create <conan-recipe-path>/musl/1.1.18 -pr <yourprofilename> includeos/test


Building llvm stdc++ stdc++abi and libunwind
--------------------------------------------

If these recipes do not have a fixed version in the conan recipe then you have to specify it alongside the ``user/channel`` as ``package/version@user/channel`` otherwise you can use the same format at musl above.

::
    $ conan create <conan-recipe-path>/llvm/libunwind -pr <yourprofilename> libunwind/7.0.1@includeos/test
    $ conan create <conan-recipe-path>/llvm/libcxxabi -pr <yourprofilename> libcxxabi/7.0.1@includeos/test
    $ conan create <conan-recipe-path>/llvm/libcxx -pr <yourprofilename> libcxx/7.0.1@includeos/test
