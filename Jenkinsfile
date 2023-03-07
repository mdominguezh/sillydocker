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
        sshagent(credentials : ['deployserver']) {
            sh 'ssh -o StrictHostKeyChecking=no roche@192.168.168.59 uptime'
            sh 'ssh -v roche@192.168.168.59'
            sh "ssh roche@192.168.168.59 /opt/roche/home/deployimage.sh sillydocher 1.${BUILD_NUMBER}"
        }
      }
    }
  }
  post {
    always{
      sh 'docker logout'
    }
  }
}
