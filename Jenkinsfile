pipeline {
    agent any

    environment {
        RECIPIENT = 'dineshravinathcloud01@gmail.com'  // Change to your email
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run Script') {
            steps {
                sh 'chmod +x hello.sh'
                sh './hello.sh'
            }
        }
    }

    post {
        success {
            emailext(
                subject: "SUCCESS: ${env.JOB_NAME} Build #${env.BUILD_NUMBER}",
                body: "Build succeeded!\n\nCheck console: ${env.BUILD_URL}console",
                to: "${env.RECIPIENT}"
            )
        }
        failure {
            emailext(
                subject: "FAILED: ${env.JOB_NAME} Build #${env.BUILD_NUMBER}",
                body: "Build failed!\n\nCheck console: ${env.BUILD_URL}console",
                to: "${env.RECIPIENT}"
            )
        }
    }
}
