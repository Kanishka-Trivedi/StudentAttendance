pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Clone Code') {
            steps {
                echo 'Code cloned from GitHub'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success { echo 'Build Successful!' }
        failure { echo 'Build Failed!' }
    }
}