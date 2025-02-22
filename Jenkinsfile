pipeline {
    agent {
        node {
            label 'maven'
        }
    }

environment {
    PATH = "/opt/apache-maven-4.0.0-alpha-10/bin:$PATH"
}
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarCloud analysis') {
    steps {
        withSonarQubeEnv('sonarqube-server') {
            sh 'mvn sonar:sonar -Dsonar.organization=devops-sonar-jenkins -Dsonar.projectKey=devops-sonar-jenkins -Dsonar.host.url=https://sonarcloud.io/'
        }
    }
    }

    }
}


