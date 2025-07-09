pipeline {
    agent any

    environment {
        RECIPIENT = 'dineshravinathcloud01@gmail.com'
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

        // 👇 Correct placement of Email Test stage inside stages block
        stage('Email Test') {
            steps {
                script {
                    emailext(
                        subject: 'Manual Email Test from Jenkins Pipeline',
                        body: 'This is a pipeline-triggered test email.',
                        to: "${env.RECIPIENT}"
                    )
                }
            }
        }
    }
}
