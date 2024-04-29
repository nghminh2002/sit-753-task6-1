pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "compile and package code"
                sh 'npm run build'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "run unit tests with Jest"
                sh 'npm test'
                echo "run integration tests with Cypress"
                sh 'npx cypress run'
            }
            post {
                success {
                    emailext body: 'Unit and Integration Tests passed. Please find attached logs.', subject: 'Unit and Integration Tests Passed', to: 's220466717@deakin.edu.au'
                }
                failure {
                    emailext body: 'Unit and Integration Tests failed. Please find attached logs.', subject: 'Unit and Integration Tests Failed', to: 's220466717@deakin.edu.au'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "code analysis with Eslint"
                sh 'npm run lint'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'security scan with SonarCloud.'
            }
            post {
                success {
                    emailext body: 'Security Scan passed. Please find attached logs.', subject: 'Security Scan Passed', to: 's220466717@deakin.edu.au'
                }
                failure {
                    emailext body: 'Security Scan failed. Please find attached logs.', subject: 'Security Scan Failed', to: 's220466717@deakin.edu.au'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "deploy to staging with AWS EC2"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "run integration test on staging with Cypress"
            }
            post {
                success {
                    emailext body: 'Integration Tests on Staging passed. Please find attached logs.', subject: 'Integration Tests on Staging Passed', to: 's220466717@deakin.edu.au'
                }
                failure {
                    emailext body: 'Integration Tests on Staging failed. Please find attached logs.', subject: 'Integration Tests on Staging Failed', to: 's220466717@deakin.edu.au'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "deploy to production with AWS EC2"
            }
        }
    }
}
