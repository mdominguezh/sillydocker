pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred-mdom')
  }
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
      agent any
      steps {
        sh 'docker build -f Dockerfile -t manueldominguezherrera464/sillydocker:latest .'
      }
    }

    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PWD | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push manueldominguezherrera464/sillydocker:latest'
      }
    }

  }
}
