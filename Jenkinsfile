pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from Git'
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling Java code'
                bat 'javac Hello.java'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Java program'
                bat 'java Hello'
            }
        }
    }

    post {
        success {
            echo 'Build successful – archiving artifacts'
            archiveArtifacts artifacts: '**/*.class', fingerprint: true
        }
        failure {
            echo '❌ Build failed – please check errors'
        }
        always {
            echo 'Pipeline execution completed'
        }
    }
}


