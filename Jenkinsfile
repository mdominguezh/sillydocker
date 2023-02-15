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
        sh 'ls -lHA '
      }
    }

    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'docker build -f sillydocker/Dokerfile .'
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