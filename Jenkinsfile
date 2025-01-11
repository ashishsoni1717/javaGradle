pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/ashishsoni1717/javaGradle.git'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub
                git branch: 'master', url: env.REPO_URL
            }
        }

        stage('Build') {
            steps {
                // Build project using Gradle
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                // Run tests
                sh './gradlew test'
            }
        }

        stage('Archive') {
            steps {
                // Archive build artifacts
                archiveArtifacts artifacts: '**/build/libs/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy steps here (e.g., copy files, run scripts)'
            }
        }
    }

    post {
        always {
            // Clean up workspace
            cleanWs()
        }
    }
}
