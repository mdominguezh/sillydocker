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

  }
}