pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred-mdom')
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
    /*
    stage('Deploy') {
      
      steps {
        sshagent(['deployserver2']) {
          sh """ssh -o StrictHostKeyChecking=no -l roche 192.168.168.60 'echo \"roche\" | /usr/bin/sudo -S /opt/roche/home/deployimage.sh sillydocker 1.${BUILD_NUMBER}'"""
        }
      }
    }   */
  }
  post {
    always{
      sh 'docker logout'
    }
  }
}
