pipeline {
  agent any
  stages {
    stage('Ckeckout Code') {
      steps {
        git(url: 'https://github.com/mdominguezh/sillydocker.git', branch: 'main')
      }
    }

    stage('List files') {
      steps {
        sh 'ls -lhA '
      }
    }

    stage('Build') {
      parallel {
        stage('Build') {
          agent any
          steps {
            sh 'docker build -f Dockerfile .'
          }
        }

        stage('Whoami') {
          steps {
            sh 'whoami'
          }
        }

      }
    }

  }
}