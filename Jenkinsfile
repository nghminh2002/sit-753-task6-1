pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "compile and package code"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "run unit tests with Jest"
                echo "run integration tests with Cypress"
            }
            post {
                always {
                    script {
                        emailext body: "Build ${currentBuild.result}: ${env.JOB_NAME} #${env.BUILD_NUMBER}\n\nConsole output is attached.", 
                                subject: "${env.JOB_NAME} #${env.BUILD_NUMBER}: Build ${currentBuild.result}: ", 
                                mimeType: 'text/html', to: 's220466717@deakin.edu.au', 
                                attachLog: true
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "code analysis with Eslint"
            }
        }
        stage('Security Scan') {
            steps {
                echo 'security scan with SonarCloud.'
            }
            post {
                always {
                    script {
                        emailext body: "Build ${currentBuild.result}: ${env.JOB_NAME} #${env.BUILD_NUMBER}\n\nConsole output is attached.", 
                                subject: "${env.JOB_NAME} #${env.BUILD_NUMBER}: Build ${currentBuild.result}: ", 
                                mimeType: 'text/html', to: 's220466717@deakin.edu.au', 
                                attachLog: true
                    }
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
                always {
                    script {
                        emailext body: "Build ${currentBuild.result}: ${env.JOB_NAME} #${env.BUILD_NUMBER}\n\nConsole output is attached.", 
                                subject: "${env.JOB_NAME} #${env.BUILD_NUMBER}: Build ${currentBuild.result}: ", 
                                mimeType: 'text/html', to: 's220466717@deakin.edu.au', 
                                attachLog: true
                    }
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
