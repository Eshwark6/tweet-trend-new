pipeline {
    agent {
        node {
            label 'maven'
        }
    }

Environment {
    PATH = $PATH:/opt/apache-maven-4.0.0-alpha-10/bin
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            steps {
                
            }
        }
    }
}
