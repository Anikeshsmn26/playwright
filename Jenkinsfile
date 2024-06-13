pipeline {
    agent any

    tools {
        nodejs "nodejs-lts" // This should match the NodeJS installation name in Jenkins
    }
     options {
        cleanWs() // Clean the workspace before starting the build
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Anikeshsmn26/playwright.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat  'npm install'
            }
        }

        stage('Run Playwright Tests') {
            steps {
                bat  'npx playwright test'
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
