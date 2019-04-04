.. _Introduction:


Introduction
~~~~~~~~~~~~

IncludeOS is an open source unikernel operating system project project designed for cloud services.
It is a minimal tasking library written in C++ which allows users to run applications written in C++ without an operating system. IncludeOS adds operating system functionality to an application by deploying a minimal virtual machine to run the application. Adding ``#include <os>`` to ``c++`` code like this:

::

    #include <os>

    int main() {
      printf("Hello World! \n");
    }

This literally includes a minimal operating system into the service during link-time. The way this works is that during link time the build system extracts service requirements from the pre-compiled OS-library and forms a single binary. To learn more about our open source project and it's potential uses visit the `technology <https://www.includeos.org/technology.html>`__ page over at our website.

.. toctree::
   :hidden:

   Features
   Tools
   Examples
   Using-memdisks
