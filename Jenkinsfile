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
               withMaven(jdk: 'JDK.1.8.0_222', maven: 'maven') {
               sh 'mvn test'
             }  
            }
        }
        stage('CodeAnalysis') { 
            steps {
               withMaven(jdk: 'JDK.1.8.0_222', maven: 'maven') {
               sh 'mvn verify sonar:sonar \
                   -Dsonar.projectKey=maven-pro \
                   -Dsonar.organization=itrainwo \
                   -Dsonar.host.url=https://sonarcloud.io \
                   -Dsonar.login=474017bb7a9a6cca9a2d66bfa02f6fc2068c0877'
                }  
            }
        }
        stage('Package') { 
            steps {
              withMaven(jdk: 'JDK.1.8.0_222', maven: 'maven') {
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
