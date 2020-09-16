pipeline {
    agent any
    stages {
        stage('Test PR') {
            when {
                expression { env.BRANCH_NAME == 'master' }
            }
            steps {
                echo 'Here would be some tests'
                sh 'printenv'
            }
        }
        stage('Deploy code to test env') {
            when {
                expression { env.BRANCH_NAME == 'develop' }
            }
            steps {
                    echo 'Here would be deployment'
                    sh 'printenv'
            }
        }
    }
}
