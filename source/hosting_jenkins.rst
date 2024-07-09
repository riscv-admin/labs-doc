==================================
Hosting RISC-V CI through Jenkins
==================================

This page describes how users can host RISC-V CI via Jenkins. For hosting CI through Jenkins, follow the steps described below.

Installing Jenkins
===================

Jenkins install instructions are given at `this link <https://www.jenkins.io/doc/book/installing/>`_.

If you wish to build Jenkins from source, the repository is available at `<https://github.com/jenkinsci/jenkins>`_

Adding RISC-V agents in Jenkins
===============================

Agents are the compute instances in Jenkins on which CI builds are run.
Once Jenkins is installed, the next step is to add RISC-V agents in Jenkins. They are also referred to as slaves, build executors, or runners.

Make sure that Jenkins Master (the compute instance on which Jenkins web server is running) is accessible by the RISC-V compute instance you wish to add as a slave.

*For the sake of simplicity, it is assumed that RISC-V compute instances have Linux operating installed on them (preferably Ubuntu) and are accessible through SSH*

Install prerequisites
---------------------

Compute instances need OpenJDK 17 or newer installed on them to be hosted on Jenkins.

.. code::

    sudo apt install openjdk-17-jdk


Set up agent in Jenkins
-----------------------

* In the Jenkins web server, go to :code:`Build Executor Status > New Node`

.. image:: assets/hosting_jenkins_1.png

.. image:: assets/hosting_jenkins_2.png

* Add a Node name (this will be displayed in the build executor list) and select Permanent Agent

* Add a suitable description for users who will be using that compute instance

.. image:: assets/hosting_jenkins_3.png

* Add the number of executors (this indicates how many builds can run concurrently)
* Change :code:`Launch method` to :code:`Launch agents via SSH` since our agent is accessible via SSH
* In :code:`Host`, add the IP or URL which can be used to access the compute instance
* In :code:`Credentials`, click on :code:`Add` if you have not created the credentials yet and add the credentials :code:`Kind` as :code:`Username with password` (these are the credentials which you can use to SSH to your RISC-V compute instance)
* In :code:`Host Key Verification Strategy`, select :code:`Manually trusted key Verification strategy` and also check :code:`Require manual verification of initial connection`
* If you access the RISC-V compute instance through a port other than 22, click on :code:`Advanced` and enter :code:`Port`
* Leave other settings as is and click save

Once the settings are saved, you will see :code:`Trust SSH Host Key` on the left bar. Click on it and grant permission to use the compute instance to the Jenkins controller.

.. image:: assets/hosting_jenkins_4.png

.. image:: assets/hosting_jenkins_5.png

Now the Jenkins agent is added and can be used. For using Jenkins as mentioned above instance, use the name which you gave it at the start in your build pipelines of Jenkins.
