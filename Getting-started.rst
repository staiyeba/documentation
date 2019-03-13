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

- Cmake
- Clang version: ``6.0``
- GCC version: ``gcc-7``
- [Conan](https://github.com/conan-io/conan)

To get help with your conan setup follow the instruction at
:ref:``Conan Configuration <Conan configs>``

Build IncludeOS
~~~~~~~~~~~~~~~

To build IncludeOS with our conan packages you will need:
- A [Profile](https://github.com/includeos/conan_config/profiles)
- Access to our built conan packages

To get access to the packages add our Artifactory to your conan remote list:

::

  $ conan remote add includeos-test https://api.bintray.com/conan/includeos/test-packages


Compilers
---------

Currently we are building IncludeOS on Linux with ``clang-6.0`` and ``gcc-7.3``.
All our dependencies, libraries and tools found on the artifactory are built
and test with these two compilers.

Building on Linux
-----------------

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

Building on MacOS
-----------------

.. needs to be added from notes
