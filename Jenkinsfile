pipeline {
    agent none
    environment {
       registry = "my_registry/some_name"
       credentialsRegistry = 'my_registry_crednetials'
    }
    stages {
        stage('Build application') {
            agent {
                docker {
                    image 'maven:3.6-openjdk-15'
                }
            }
            steps {
                echo 'Here would be application build'
                sh 'mkdir -p ${WORKSPACE}/src/java_app'
                sh 'cp -r ${WORKSPACE}/* ${WORKSPACE}/src/java_app'
                sh 'cd ${WORKSPACE}/src/java_app | mvn package'
            }
        }
        stage('Test code on pull requests') {
            agent {
                  docker {
                       image 'maven:3.6-openjdk-15'
                   }
            }
            when {
                expression { env.BRANCH_NAME =~ 'PR.*' }
            }
            steps {
                echo 'Here would be tested pull request'
                sh 'mkdir -p ${WORKSPACE}/src/java_app'
                sh 'cp -r ${WORKSPACE}/* ${WORKSPACE}/src/java_app'
                sh 'cd ${WORKSPACE}/src/java_app | mvn test'
            }
        }
        stage('Build docker image and deploy code to test environment') {
            when {
                expression { env.BRANCH_NAME == 'develop' }
            }
            steps {
                script {
                    def dockerImageRevision = "${env.GIT_COMMIT.substring(0,6)}"
                    def appimage = docker.build registry + ":${dockerImageRevision}"
                    docker.withRegistry( registry, credentialsRegistry ) {
                       appimage.push()
                       appimage.push('latest')
                    }
                    sh 'sed -i "s/tagVersion/${dockerImageRevision}/g" ${WORKSPACE}/kubernetes/deploy_file.yml'
                    sh 'kubectl apply -f ${WORKSPACE}/kubernetes/. --namespace=test'
                }
            }
        }
        stage('Deploy code to production') {
            when {
                expression { env.BRANCH_NAME == 'master' }
            }
            steps {
                script {
                    git credentialsId: 'github', url: 'https://github.com/czikit12/audibene_recruitment'
                    sh "git checkout origin/develop"
                    def developRev = sh(returnStdout: true, script: 'git log -1 --pretty=format:"%h"')
                    sh 'sed -i "s/tagVersion/${developRev}/g" ${WORKSPACE}/kubernetes/deploy_file.yml'
                    sh 'kubectl apply -f ${WORKSPACE}/kubernetes/. --namespace=prod'
                }
            }
        }
    }
}
