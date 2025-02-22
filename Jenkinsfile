pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('CLone-code') {
            steps {
                git branch: 'main', url: 'https://github.com/Eshwark6/tweet-trend-new.git'
            }
        }
    }
}
