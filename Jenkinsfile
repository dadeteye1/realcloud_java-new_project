pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/dadeteye1/realcloud_java-new_project.git'
            }
        }
        stage('Build') {
            steps {
                sh 'SampleWebApp && mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'cd SampleWebApp mvn test'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat9', path: '', url: 'http://18.227.10.109:8080//')], contextPath: 'path', war: '**/*.war'
            }
        }
    }
}