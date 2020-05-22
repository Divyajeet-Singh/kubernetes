pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/Divyajeet-Singh/kubernetes.git', poll: true, credentialsId: 'H/15 * * * *', branch: 'master')
      }
    }

  }
}