pipeline {
    agent any
    tools { maven 'maven3' }
    
    environment {
        GIT_CREDENTIALS_ID = "2dee6608-a49a-4ab0-90c0-3836e8f88c3b" // Use the ID from Step 1
        GIT_REPO = 'https://github.com/rajadevops2025/mavendemo.git'
        GIT_BRANCH = 'main'
    }
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: GIT_BRANCH, credentialsId: GIT_CREDENTIALS_ID, url: GIT_REPO
                }
            }
        }
        stage('Build') {
            steps { bat 'mvn clean package' }
        }
        stage('Archive') {
            steps { archiveArtifacts artifacts: 'target/*.jar', fingerprint: true }
        }
    }
}
