pipeline {
  agent any
  stages {
    
    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/hydave25/simplegoapp.git', branch: 'master', credentialsId: 'github Token for Jenkins'])
    }
    stage('Build') {
      steps {
        echo 'Building..'
      }
    }

    stage('Test') {
      steps {
        echo 'Testing..'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying....'
      }
    }

  }
}
