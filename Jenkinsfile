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
        sh 'ls ${WORKSPACE}; echo ${WORKSPACE}'
        sh 'ls ${JENKINS_HOME}; echo ${JENKINS_HOME}'
      }
    }
/*
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
        sshagent(['deployserver2']) {
          sh """ssh -o StrictHostKeyChecking=no -l roche 192.168.168.60 'echo \"roche\" | /usr/bin/sudo -S /opt/roche/home/deployimage.sh sillydocker 1.${BUILD_NUMBER}'"""
        }
      }
    }*/
     stage('ZIP') {
      steps {
        sh 'pwd'
        zip zipFile: 'Test.zip', archive: false, dir: '.', glob: "*-acceptance-test/src/test/resources/features*,**/TEST-*xml"
        archiveArtifacts artifacts: 'Test.zip', fingerprint: true
      }
    }
  }/*
  post {
    always{
      sh 'docker logout'
    }
  }*/
}
