 pipeline {
  agent none

  stages {
    stage('Linting') {
      agent {
        docker {
          image 'cytopia/ansible-lint'
          args '--entrypoint='
        }
      }
      steps {
        script {
          try {
            sh 'ansible-lint *.yaml'
          } catch (err) {
            echo err.getMessage()
            unstable('Linting failed')
          }
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

