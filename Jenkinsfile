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
              script { 
                   dockerImage = docker.build registry + ":$BUILD_NUMBER" 
               }
           }
}
        stage('Deploy our image') { 
            steps { 
                echo 'Deploying our image..'
                script { 
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push() 
                    }
                } 
            }
        }

        stage('Cleaning up') { 
            steps { 
                sh "docker rmi $registry:$BUILD_NUMBER" 
            }
        } 
