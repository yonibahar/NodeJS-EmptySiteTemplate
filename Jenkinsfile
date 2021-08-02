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

  }
}