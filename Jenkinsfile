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
        sh "docker build -f Dockerfile -t manueldominguezherrera464/sillydocker:1.${BUILD_NUMBER} ."
      }
    }

    stage('Login') {
      steps {
        sh 'docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW'
      }
    }

    stage('Push') {
      steps {
        sh "docker push manueldominguezherrera464/sillydocker:1.${BUILD_NUMBER}"
      }
    }
    stage('Deploy') {
      steps {
        sh 'apt update -y && apt install wget -y && wget -P ~/ https://github.com/clarkwang/passh/master.zip && cc -o passh passh.c && cp -v passh /usr/bin/ && passh -h '     
      }
    }
  }
  post {
    always{
      sh 'docker logout'
    }
  }
}
