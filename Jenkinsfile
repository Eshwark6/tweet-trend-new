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
    }
}
