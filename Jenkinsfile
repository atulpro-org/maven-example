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
                -Dsonar.projectKey=atulpro-org.maven-example \
                -Dsonar.organization=itrainwo \
                -Dsonar.host.url=https://sonarcloud.io \
                -Dsonar.login=ae48572f01196661f817ce2cc45b7a84f2dcb0ae'
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
