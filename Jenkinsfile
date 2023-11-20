pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube-9.9.2') {
                    script {
                        def sonarScannerHome = tool 'SonarQubeScanner';
                        sh "${sonarScannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
        stage('Results') {
            steps {
                echo 'View SonarQube analysis results: http://34.150.235.54:9000/projects'
            }
        }
    }
}
