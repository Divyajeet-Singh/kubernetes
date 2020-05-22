pipeline {
  agent any
  stages {
    stage('Build') {
      agent {
        docker {
          image 'httpd'
        }

      }
      steps {
        git(url: 'https://github.com/Divyajeet-Singh/kubernetes.git', branch: 'master')
      }
    }

  }
}