.. _Jenkins CI:

CI Pipeline for Developers
==========================

We use continuous integration to build and test our projects on a regular basis.
You will find all the repositories currently using CI under the
IncludeOS Github Organization on our Jenkins server.

Jenkins CI
~~~~~~~~~~

Build Node: `Jenkins-public.includeos.org <https://jenkins-public.includeos.org/job/IncludeOS/>`__
---------------------------------------------------------------------------------------------------


Personal builds on the Jenkins server
-------------------------------------

If you want to get your personal fork of IncludeOS to build with every commit
this procedure will show you what steps to go through.

**Things to take note off:**

- Will look for the repo: ``https://github.com/<github-username>/IncludeOS``

- Does not merge with upstream automatically unless approved by an IncludeOS developer.


Setting up the Webhook
----------------------

Follow these steps to get it to work:

1. Go to the settings page for your **personal fork**

|Settings menu|

2. Navigate to the *Webhooks & Services* section and press the *Add webhook* button. Then enter the following url into the *Payload URL* section ``https://jenkins.includeos.org/github-webhook/``. Then press *Add webhook*

|Payload URL|

3. To make sure this works, go back to the webhooks page and make sure you see the green checkmark next to the url. This might take a few seconds, so refresh the page.

|Checkmark|

Then when the tests are complete, the results will be available on `jenkins-public.includeos.org <https://jenkins-public.includeos.org>`__

.. |Settings menu| image:: http://i.imgur.com/wfoYcaD.png
.. |Payload URL| image:: http://i.imgur.com/g0gEcBq.png
.. |Checkmark| image:: http://i.imgur.com/yUTIwZ1.png?1

Travis CI
~~~~~~~~~

We have recently started using `Travis CI <https://travis-ci.org/includeos>`__ to build and upload some of our dependencies for macos. We are also building and
testing deploy for our `homebrew-includeos` project.
