pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Postman Tests') {
            steps {
                sh './scripts/run-newman.sh'
            }
        }

        stage('Publish Reports') {
            steps {
                publishHTML([
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'reports/newman',
                    reportFiles: 'report.html',
                    reportName: 'Newman Test Report'
                ])
            }
        }
    }
}