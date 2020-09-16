node {
  checkout scm
  def workspace = pwd()

  if (env.BRANCH_NAME == 'master') {
    stage ('Some Stage 1 for master') {
      echo "master"
    }
    stage ('Another Stage for Master') {
     echo "Second stage"
    }
  }

  else if (env.BRANCH_NAME == 'stage') {
    stage ('Some stage branch step') {
      sh 'do something'
    }
    stage ('Deploy to stage target') {
      sh 'do something else'
    }
  }

  else {
    sh 'echo "Branch not applicable to Jenkins... do nothing"'
  }
}