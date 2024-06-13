pipeline {
    agent any

    tools {
        nodejs "nodejs-lts" // This should match the NodeJS installation name in Jenkins
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
                sh 'npx playwright test'
            }
        }
    }

    post {
        always {
            junit 'playwright-report/*.xml'
            archiveArtifacts 'playwright-report/**/*'
        }
    }
}
