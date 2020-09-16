pipeline {
    agent any
    environment {
       registry = "my_refistry/some_name"
    }
    stages {
 //       stage('Test') {
 //           steps {
 //               echo 'TEST COMMANDSs'
 //           }
 //       }
        stage('Test PR') {
 /*           agent {
              docker {
                   image 'nodejs'
               }
            }
 */
            when {
                expression { env.BRANCH_NAME =~ 'PR.*' }
            }
            steps {
                echo 'Here would be some tests'
                sh 'printenv'
            }
        }
        stage('Deploy code to test env') {
            environment {
               registryCredential = 'my_registry_crednetials'
            }
/*            when {
                expression { env.BRANCH_NAME == 'develop' }
            }
 */
            steps {
                    echo 'Here would be deployment of test application'
                script {
                    dockerImageRevision = "${env.GIT_COMMIT}.substring(0,7)"
                    println "${dockerImageRevision}"
                }
            }
        }
        stage('Deploy code to production env') {
            when {
                expression { env.BRANCH_NAME == 'master' }
            }
            steps {
                    echo 'Here would be deployment of production env'

            }
        }
    }
}
