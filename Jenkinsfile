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

    stage('Email Test') {
  steps {
    script {
      emailext(
        subject: 'Manual Email Test from Jenkins Pipeline',
        body: 'This is a pipeline-triggered test email.',
        to: 'dineshravinathcloud01@gmail.com'
      )
    }
  }
}
}
