pipeline {
    agent any
    sh 'printenv'
    stages {
        stage('Test PR') {
            when {
                expression { env.BRANCH_NAME == 'PR*' }
            }
            steps {
                echo 'Here would be some tests'

            }
        }
        stage('Deploy code to test env') {
            when {
                expression { env.BRANCH_NAME == 'develop' }
            }
            steps {
                    echo 'Here would be deployment of test application'

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
