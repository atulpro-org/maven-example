pipeline {
    agent any 
    stages {
        stage('Code Checkout') { 
            steps {
                git credentialsId: 'maven', url: 'https://github.com/atulpro-org/maven-example.git/'
            }
        }
        stage('Build') { 
            steps {
                withMaven(jdk: 'JDK.1.8.0_222', maven: 'maven') {
                    sh 'mvn clean compile'
                }
            }
        }
        stage('Test') { 
            steps {
               withMaven(jdk: 'JDK', maven: 'Maven') {
               sh 'mvn test'
             }  
            }
        }
        stage('Package') { 
            steps {
              withMaven(jdk: 'JDK', maven: 'Maven') {
               sh 'mvn package'
             }  
            }
        }
        stage('Docker Image') { 
            steps {
             sh 'echo docker image is build'   
            }
        }
        stage('Deploy to Dev') { 
            steps {
             sh 'echo Deploy to Dev'   
            }
        }
        stage('Deploy to prod') { 
            steps {
              sh 'echo Deploy to Prod'  
            }
        }
    }
}
