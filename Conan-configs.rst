.. _Conan configs:

Conan Configuration for IncludeOS
=================================

Getting IncludeOS Conan Configs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We have set up a repository ([includeos/conan_config](https://github.com/includeos/conan_config))
that helps IncludeOS users configure all the necessary
conan settings. To configure using this repo just do:

::

    $ conan config install https://github.com/includeos/conan_config.git


This adds our remote artifactory in your conan remotes and also installs all the
profiles we have in the repository for you.

Profiles
~~~~~~~~

Conan uses [profiles](https://docs.conan.io/en/latest/reference/profiles.html)
to build packages. By default IncludeOS will build with ``clang 6.0`` if
``CONAN_PROFILE`` is not defined. Passing ``-DCONAN_DISABLE_CHECK_COMPILER``
during build disables this check.

Profiles we are developing with can be found in [includeos/conan_config](https://github.com/includeos/conan_config) repository under ``conan_config/profiles/ ``.
If you have not used the  ``conan config install`` command above, then to install the profiles, copy them over to your user  ``./conan/profiles`` folder.

The target profiles we have verified are the following:
- [clang-6.0-linux-x86](https://github.com/includeos/conan_config/tree/master/profiles/clang-6.0-linux-x86)
- [clang-6.0-linux-x86_64](https://github.com/includeos/conan_config/tree/master/profiles/clang-6.0-linux-x86_64)
- [gcc-7.3.0-linux-x86_64](https://github.com/includeos/conan_config/tree/master/profiles/gcc-7.3.0-linux-x86_64)
- [clang-6.0-macos-x86_64](https://github.com/includeos/conan_config/tree/master/profiles/clang-6.0-macos-x86_64)

To ensure the profile/s has been installed do:

::
    $ conan profile list


Verify the content of your profile by:

::
    $ conan profile show <yourprofilename>


If your profile is on the list and contents are verified, you are set to use the
profile for building.

IncludeOS Artifactory Repo
~~~~~~~~~~~~~~~~~~~~~~~~~~

The artifactory repository is where all the packages used to build IncludeOS
are uploaded. Adding the repo to your conan remotes will give you access to all
our packages developed for IncludeOS.

You check your repository remotes, do:

::
    $ conan remote list


If the includeOS-Develop remote is not added do, you have to add it.

To add the IncludeOS-Develop conan Artifactory repository to your conan remotes:

::
    $ conan remote add includeos-test https://api.bintray.com/conan/includeos/test-packages

.. toctree::
  :hidden:

  Conan-package-build
