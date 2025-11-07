pipeline {
    agent any
    tools { 
        maven 'Maven'  
    }

    stages {
        stage('SCM') {
            steps {
                echo 'Hello Clone stage'
                git branch: 'main', url: 'https://github.com/kottachandrasekhar/chandu.git'
                }
        }
        stage('Build') {
            steps {
                echo 'Hello Build'
                sh 'mvn clean install'
            }
        }
        stage('Dev-Deploy') {
            steps {
                echo 'Hello Docker Deploy'
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '107ca4f1-05fb-4e7a-9cea-20694d984786', path: '', url: 'http://192.168.106.131:8081/')], contextPath: 'chandu.war', war: '**/*.war' 
                  }
        }
}
}
