pipeline {
  agent any
  stages {
    stage('Check Out Code') {
      steps {
        git(url: 'https://github.com/yonibahar/NodeJS-EmptySiteTemplate.git', branch: 'master', changelog: true, poll: true)
      }
    }

    stage('Build & Compile') {
      steps {
        sh 'nvm install'
      }
    }

  }
}