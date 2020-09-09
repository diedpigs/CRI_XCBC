 pipeline {
  agent none

  stages {
    stage('Linting') {
      agent {
        docker {
          image 'cytopia/ansible-lint'
          args '--volume=${PWD}:/data'
        }
      }
      post {
        success {
          echo 'Linting success'
        }
        unstable {
          echo 'Linting failed'
        }
      }
    }
  }
}

