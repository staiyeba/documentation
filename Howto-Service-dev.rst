.. _Howto Service dev:

Service Developers guide
========================



Starting an IncludeOS Instance
------------------------------





Building a Service
------------------



Creating your own service
-------------------------

Writing your first service

To start writing your first service,
- Copy the [demo_service/service.cpp](https://github.com/includeos/demo-examples/blob/master/demo_service/service.cpp) example.
- Then start implementing the `Service::start` function in the `Service` class, located in `<your-service-name>/service.cpp` (very simple example provided). This function will be called once the OS is up and running.
- Update the `CMakeLists.txt` to specify the name of your project, enable any needed drivers or plugins, etc.
- Update the `conanfile.txt` to specify any build requirements and generators.

You should then be able to run your service in the same way as the demo_service.

To add a new service to our demo examples, make a PR to our [demo-examples](https://github.com/includeos/demo-examples) repo. Make sure to
add a README in your example folder with description of your service.


> **Note:** Remember to deactivate your service environment after your work with:

::

    $ source deactivate.sh


Uploading your Service to bintray
---------------------------------
