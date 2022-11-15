pipeline {
    agent any
    
    tools {
        maven 'M2_HOME'
    }

    stages {
        stage('Checkout') {
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/prashantsuragimath/JenkinsPipelineDemo.git']]])
            }
        }
        stage('Build') {
            steps {
            sh 'mvn clean compile'
            }
        }  
        stage('Test') {
            steps {
            sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
            sh 'mvn clean package'
            }
        } 
        stage('Deploy') {
            steps {
               deploy adapters: [tomcat9(credentialsId: '7b5b7950-998d-4f7b-9331-8f1f19d8741b', path: '', url: 'http://65.0.19.152:8081/')], contextPath: null, war: '**/.*war'
                
            }
        }
    }
}
