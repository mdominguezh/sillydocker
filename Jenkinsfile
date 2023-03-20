pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-cred-mdom')
    SSH_PRIVATE_KEY = """-----BEGIN OPENSSH PRIVATE KEY-----
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
-----END OPENSSH PRIVATE KEY-----"""
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
        sh "ssh-add - <<< ${SSH_PRIVATE_KEY}"
        sh "ssh -o StrictHostKeyChecking=no roche@192.168.168.59 uptime"
      }
    }
  }
  post {
    always{
      sh 'docker logout'
    }
  }
}
