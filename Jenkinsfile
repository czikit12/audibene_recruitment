pipeline {
    agent any
    environment {
       registry = "my_refistry/some_name"
    }
    stages {
        stage('Build application') {
/*
            agent {
                docker {
                    image 'maven:3.6-openjdk-15'
                }
            }
*/
            steps {
/*
                sh 'mkdir -p ${WORKSPACE}/src/java_app'
                sh 'cp -r ${WORKSPACE}/* ${WORKSPACE}/src/java_app'
                sh 'cd ${WORKSPACE}/src/java_app | mvn package'
*/
                script {
                    // The below will clone your repo and will be checked out to master branch by default.
                    git credentialsId: 'github', url: 'https://github.com/czikit12/audibene_recruitment'
                    // Do a ls -lart to view all the files are cloned. It will be clonned. This is just for you to be sure about it.
                    sh "ls -lart ./*"
                    // List all branches in your repo.
                    def developRev = sh 'git log -1 --pretty=format:"%h"'
                    println(developRev)
                }
            }
        }
        stage('Test pull requests') {
 /*
            agent {
                  docker {
                       image 'maven:3.6-openjdk-15'
                   }
            }
 */
            when {
                expression { env.BRANCH_NAME =~ 'PR.*' }
            }
            steps {
                echo 'Here would be tested pull request'

/*
                sh 'mkdir -p ${WORKSPACE}/src/java_app'
                sh 'cp -r ${WORKSPACE}/* ${WORKSPACE}/src/java_app'
                sh 'cd ${WORKSPACE}/src/java_app | mvn test'
*/
            }
        }
        stage('Deploy code to test env') {
            environment {
               credentialsRegistry = 'my_registry_crednetials'
            }
            when {
                expression { env.BRANCH_NAME == 'develop' }
            }

            steps {
                    echo 'Here would be deployment of test application'
                    sh 'printenv'
/*
                script {

                    def dockerImageRevision = "${env.GIT_COMMIT.substring(0,6)}"
                    def appimage = docker.build registry + ":${dockerImageRevision}"
                    docker.withRegistry( '', credentialsRegistry ) {
                       appimage.push()
                       appimage.push('latest')
                    }
                }
*/
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
