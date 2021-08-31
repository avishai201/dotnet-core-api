pipeline {
  agent {
    node {
      label 'docker-vm'
    }

  }
  stages {
    stage('Check Out Code') {
      steps {
        git(url: 'https://github.com/avishai201/dotnet-core-api.git', branch: 'master', changelog: true, poll: true)
      }
    }

    stage('Build Image of Docker') {
      steps {
        sh 'docker build -t avishai201/todoapi:${BUILD_ID} .'
      }
    }

  }
}