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
               sh "scp -v -o StrictHostKeyChecking=no **/*.war root@${params.staging_server}:/opt/tomcat/webapps/"
                
            }
        }
    }
}
