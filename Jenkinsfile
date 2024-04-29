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
                        def consoleOutputFile = "${env.WORKSPACE}/console_output.txt"

                        writeFile file: consoleOutputFile, text: currentBuild.rawBuild.getLog(1000)

                        emailext body: "Build ${currentBuild.result}: ${env.JOB_NAME} #${env.BUILD_NUMBER}\n\nConsole output is attached.", 
                                subject: "Build ${currentBuild.result}: ${env.JOB_NAME} #${env.BUILD_NUMBER}", 
                                mimeType: 'text/html', to: 'your_email@example.com', 
                                attachmentsPattern: consoleOutputFile
                    }
                }
            }
        }
        // stage('Code Analysis') {
        //     steps {
        //         echo "code analysis with Eslint"
        //     }
        // }
        // stage('Security Scan') {
        //     steps {
        //         echo 'security scan with SonarCloud.'
        //     }
        //     post {
        //         success {
        //             emailext body: 'Security Scan passed. Please find attached logs.', subject: 'Security Scan Passed', to: 's220466717@deakin.edu.au'
        //         }
        //         failure {
        //             emailext body: 'Security Scan failed. Please find attached logs.', subject: 'Security Scan Failed', to: 's220466717@deakin.edu.au'
        //         }
        //     }
        // }
        // stage('Deploy to Staging') {
        //     steps {
        //         echo "deploy to staging with AWS EC2"
        //     }
        // }
        // stage('Integration Tests on Staging') {
        //     steps {
        //         echo "run integration test on staging with Cypress"
        //     }
        //     post {
        //         success {
        //             emailext body: 'Integration Tests on Staging passed. Please find attached logs.', subject: 'Integration Tests on Staging Passed', to: 's220466717@deakin.edu.au'
        //         }
        //         failure {
        //             emailext body: 'Integration Tests on Staging failed. Please find attached logs.', subject: 'Integration Tests on Staging Failed', to: 's220466717@deakin.edu.au'
        //         }
        //     }
        // }
        // stage('Deploy to Production') {
        //     steps {
        //         echo "deploy to production with AWS EC2"
        //     }
        // }
    }
}
