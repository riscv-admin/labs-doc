Writing a CI pipeline file for Jenkins
========================================

The CI pipeline used for Jenkins CI is called Jenkinsfile. Jenkinsfile can be of two types:

1. Scripted Jenkinsfile
2. Declarative Jenkinsfile


Jenkinfile Examples
===================

Following is an example of scripted jenkinfile.

.. code-block:: groovy

    node{
        stage('*** Phase 1 ***') {
            //Using bash commands
            sh '''#!/bin/bash
                echo "Hello World !\n"
            '''
        }
    }

The above jenkinsfile prints "Hello World !" on the console output. The :code:`node` indicates the build executor where you would like to run your build. If there is nothing written with :code:`node`, the build can run on any build executor.

The above jenkinsfile can be written in Declarative syntax as below:

.. code-block:: groovy

    pipeline {
        agent any

        stages {
            stage('*** Phase 1 ***') {
                steps {
                    // Using bash commands
                    sh '''#!/bin/bash
                        echo "Hello World !\n"
                    ''' 
                }
            }
        }
    }

