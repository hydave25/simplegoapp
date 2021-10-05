Jenkinsfile (Declarative Pipeline)
pipeline {
    environment { 
        registry = "hydave25/simplegoapp"
        registryCredential = 'hydave25'
        dockerImage = ''
    }
    agent any

    stages {
        stage('Cloning our Git') { 
            steps {
                echo 'Cloning from Git Repo..'
                git 'https://github.com/hydave25/simplegoapp'
            
        }
            
            
            
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "./gradlew sonarqube"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        
        stage('Building our image') {
           steps {
              echo 'Building our image..'
            }
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
