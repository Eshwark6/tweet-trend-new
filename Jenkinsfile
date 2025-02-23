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
                echo 'building started........'
                sh 'mvn clean package -Dmaven.skip.test=true'
                echo 'building completed........'
            }

        
        }
        stage ('Testing'){
            steps {
                echo 'testing started........'
                sh 'mvn surefire-report:report'
                echo 'testing completed........'
            }
        
        }
        stage('SonarCloud analysis') {
            steps {
                withSonarQubeEnv('sonarqube-server') {
                sh 'mvn sonar:sonar -Dsonar.organization=devops-sonar-jenkins -Dsonar.projectKey=devops-sonar-jenkins -Dsonar.host.url=https://sonarcloud.io/'
        }
    }
    }
        stage("Quality Gate"){
            steps {
                script {
        timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
            def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
            if (qg.status != 'OK') {
            error "Pipeline aborted due to quality gate failure: ${qg.status}"
            }
        }
                }
        }
    }
    }
}


