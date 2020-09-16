node {
  def workspace = pwd()
   sh 'echo ${env.BRANCH_NAME}'
  if (env.BRANCH_NAME == 'master') {
    stage ('Some Stage 1 for master') {
      sh 'echo "master of disasteasdasdrsssad"'
    }
    stage ('Another Stage for Master') {
      sh 'echo "second stage of master"'
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