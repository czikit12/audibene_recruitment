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
                    def developRev = sh 'git log -1 --pretty=format:"%h" develop'
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
                script {
/*
                    def dockerImageRevision = "${env.GIT_COMMIT.substring(0,6)}"
                    def appimage = docker.build registry + ":${dockerImageRevision}"
                    docker.withRegistry( '', credentialsRegistry ) {
                       appimage.push()
                       appimage.push('latest')
*/
                    }
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
