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
        withSonarQubeEnv('SonarCloud') {
            sh 'mvn sonar:sonar -Dsonar.organization=devops-sonar-jenkins -Dsonar.projectKey=devops-sonar-jenkins -Dsonar.host.url=https://sonarcloud.io/ -Dsonar.login=7d53dc1caf140c3cba898079288eb83f1244d36b'
        }
    }
    }

    }
}


