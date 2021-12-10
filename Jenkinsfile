pipeline {
    agent any
    environment {
        PATH = "PATH=$PATH:/opt/apache-maven-3.8.4/bin"
    }
    stages {
        stage('fetch_code') {
            steps {
                git 'https://github.com/kuslapur/sonarqube.git'

            }
        }
        stage('Build') {
            steps {
               sh 'mvn clean package'    
            }
        }
        stage('Sonarqube') {
            steps {
            withSonarQubeEnv('sonarqube-8.9.3')
               sh "mvn sonar:sonar"    
            }
        }
    }
}
