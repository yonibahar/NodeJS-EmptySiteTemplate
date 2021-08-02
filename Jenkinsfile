pipeline {
  agent {
    node {
      label 'nodejs-build'
    }

  }
  stages {
    stage('CheckOut Code') {
      steps {
        git(url: 'https://github.com/lidorg-dev/NodeJS-EmptySiteTemplate.git', branch: 'master', changelog: true, credentialsId: 'github', poll: true)
      }
    }

    stage('Install Dependencies {Build}') {
      steps {
        sh 'npm install'
      }
    }

    stage('running the app') {
      steps {
        sh 'npm start &'
      }
    }

    stage('test the app ') {
      steps {
        sh '''sleep 5 && curl localhost:8080
'''
      }
    }

    stage('kill app') {
      steps {
        sh 'pkill -f node'
      }
    }

    stage('Package') {
      steps {
        sh 'zip -r package.zip .'
        archiveArtifacts(artifacts: 'package.zip', onlyIfSuccessful: true)
        cleanWs(cleanWhenSuccess: true)
      }
    }

    stage('notify slack') {
      steps {
        slackSend(channel: 'devops_kamatech', color: '#3EA652', message: "Success: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
      }
    }

  }
}
