.. _Testing :

Testing IncludeOS
=================

To test IncludeOS as a kernel and it's features, we have written a number of tests
that can be reused by anyone to test there work on IncludeOS. You will find a list
of our tests in the `IncludeOS/test <https://github.com/includeos/IncludeOS/tree/master/test>`__ folder.

.. note:: The following testing instructions only work on Linux at the moment.

Unit Tests
~~~~~~~~~~

All the tests are grouped by categories as listed in the folder. The unit tests for each of the categories of tests are located under ``IncludeOS/test/<category>/unit/<test-name>.cpp``.

To run all the unit tests simultaneously do:

::

  $ conan install IncludeOS/test -pr gcc-7.3.0-linux-x86_64 -s build_type=Debug
  $ . ./activate.sh

If you want to get the coverage report for the unit tests as well do:

::

  # cmake coverage
  $ . ./activate.sh && cmake -DCOVERAGE=ON -DCODECOV_HTMLOUTPUTDIR=<your-coverage-dir> IncludeOS/test
  # make coverage
  $ . ./activate.sh && make -j nproc coverage

After running the test, you can then view the coverage report in html format
in the path you specified.

Integration Testing
~~~~~~~~~~~~~~~~~~~

To do integration testing you will need to have all the necessary tools installed.
We use our `puppet file <https://github.com/includeos/includeos-tools/blob/master/puppet/test_client.pp>`__ to configure our test instances.
You can use the puppet manifest to install on your local machine.


To install and build the integration tests:

::

  $ conan install test/integration -pr clang-6.0-linux-x86_64
  $ . ./activate.sh
  $ cmake $SRC/test/integration -DSTRESS=ON -DCMAKE_BUILD_TYPE=Debug
  $ make -j nproc

If you would like to build the tests without setting up the network tools, you can use ``-DFOR_PRODUCTION=OFF`` with the ``cmake`` command. This is however not recommended, as keeping the production setting to ON gives proper random.

We use ``ctest`` to run the integration tests. Along with integration tests we
also have stress tests. To skip the stress tests and run only the integration
tests at random, do:

::

  $ ctest -E stress --output-on-failure --schedule-random

To run only the stress tests and skip all other tests, do:

::

  $ ctest -R stress -E integration --output-on-failure

You can have a look at our `Jenkinsfile <https://github.com/includeos/IncludeOS/blob/master/Jenkinsfile>`__ to get an overview of how we run the tests. You will notice we run our unit tests and coverage with
the gcc profile, currently thats the one we are focusing on.

.. warning:: Remember to run ``. ./deactivate.sh`` to reset your environment to previous state after testing is complete.
