.. _Howto Kernel dev:

Kernel Developers guide
=======================

Build IncludeOS
~~~~~~~~~~~~~~~

To build IncludeOS with our conan packages you will need:

- A `Profile <https://github.com/includeos/conan_config/profiles>`__
- Access to our built conan packages

To get access to the packages add our Artifactory to your conan remote list:

::

    $ conan remote add includeos-test https://api.bintray.com/conan/includeos/test-packages




Compilers
---------

Currently we are building IncludeOS on Linux with ``clang-6.0`` and ``gcc-7.3``.
All our dependencies, libraries and tools found on the artifactory are built
and test with these two compilers.

Building kernel on Linux
------------------------

To build IncludeOS on Linux for Linux with clang-6.0 you can use the profile named
``clang-6.0-linux-x86_64``:

::

    $ cmake -DCONAN_PROFILE=clang-6.0-linux-x86_64 <path to includeos repo>
    $ make
    $ make install


Cross-Platform Building
^^^^^^^^^^^^^^^^^^^^^^^

To build IncludeOS for MacOS on Linux, you can use the ``clang-6.0-macos-x86_64``
profile.


Kernel Development
------------------


Using our Packages
------------------



Developing your own Packages
----------------------------

If you are interested in editing/building our dependency packages on your own,
you can checkout our repositories at [includeos/](https://github.com/includeos/).
Some our tools and libraries are listed below under [Tools and Libraries](#libs_tools).
You can find the external dependency recipes at [includeos/conan](https://github.com/includeos/conan).
Currently we build with `clang-6` and `gcc-7.3.0` compiler toolchains.
It is expected that these are already installed on your system.

##### Building Tools

The GNU Binutils are a collection of binary tools we have added to the profiles
so that the binaries are always executable inside the conan environment.
They are not an actual part of the final binary.

The binutils package must be built for the Host it's intended to run on. Therefore
the binutils package is built using a special _toolchain profile_ that doesn't have
a requirement on binutils itself.

To build `bintuils` using our [includeos/conan](https://github.com/includeos/conan/tree/master/dependencies/gnu/binutils/2.31) recipes:

- Clone the repository
- Do `conan create` as follows:

```
conan create <binutils-conan-recipe-path>/binutils/2.31 -pr <yourprofilename>-toolchain includeos/test
```

For MacOS users, we currently have a [apple-clang-10-macos-toolchain](https://github.com/includeos/conan_config/blob/master/profiles/apple-clang-10-macos-toolchain) for building a binutils package.

##### Building Dependencies

To build our other dependencies you may use the conan recipes we have in the
[conan](https://github.com/includeos/conan) repository.

> **Note:** If you plan to build dependencies you might need to ensure you have
other missing libraries installed.

**Requirements**

- GNU C++ compiler - `g++-multilib`
- Secure Sockets Layer toolkit `libssl-dev`

###### Building musl
```
conan create <conan-recipe-path>/musl/1.1.18 -pr <yourprofilename> includeos/test
```

###### Building llvm stdc++ stdc++abi and libunwind

If these recipes do not have a fixed version in the conan recipe then you have
to specify it alongside the `user/channel` as `package/version@user/channel`
otherwise you can use the same format at musl above.

```
conan create <conan-recipe-path>/llvm/libunwind -pr <yourprofilename> libunwind/7.0.1@includeos/test
conan create <conan-recipe-path>/llvm/libcxxabi -pr <yourprofilename> libcxxabi/7.0.1@includeos/test
conan create <conan-recipe-path>/llvm/libcxx -pr <yourprofilename> libcxx/7.0.1@includeos/test
```
___

##### Building IncludeOS libraries and tools

We have moved the libraries and tools created by IncludeOS outside the IncludeOS
repository. You can now find them all in their own repositories inside the IncludeOS organization.

To build the libraries and tools,

```
  $ git clone https://github.com/includeos/mana.git
  $ cd mana
  $ conan create . includeos/latest -pr clang-6.0-linux-x86_64
```

<a name="libs_tools"></a> Below is a list of some of our Libraries/Tools:

- [Vmbuild](https://github.com/includeos/vmbuild) -
Vmbuild is an utility for building the IncludeOS virtual machines.

- [Vmrunner](https://github.com/includeos/vmrunner) -
Vmrunner is a utility developed for booting IncludeOS binanries.

- [Mana](https://github.com/includeos/mana) -
Mana is a web application framework which is used to build a IncludeOS webserver.
We have an example named [acorn](https://github.com/includeos/demo-examples/tree/master/acorn) which demonstrates mana's potential.

- [Microlb](https://github.com/includeos/microlb) -
Microlb is a library written for building the IncludeOS load balancer.
We have an example named [microlb](https://github.com/includeos/demo-examples/tree/master/microLB) which demonstrates our load balancer.

- [Diskbuilder](https://github.com/includeos/diskbuilder) -
Diskbuilder is a tool used for building disks for IncludeOS.

- [NaCl](https://github.com/includeos/NaCl) -
NaCl is the configuration language tool we have tailored for IncludeOS to allow
users to configure various network settings such as firewall rules, vlans,
ip configurations etc.

To get your packages ine Editable mode, look at the page on editable package mode.

Uploading your Packages
-----------------------







.. toctree::
   :maxdepth: 1

   Editable-mode
