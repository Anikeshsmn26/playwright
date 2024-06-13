pipeline {
    agent any

    tools {
        nodejs "NodeJS" // This should match the NodeJS installation name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Anikeshsmn26/playwright.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Playwright Tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        always {
            junit 'playwright-report/*.xml'
        }
    }
}
