pipeline {
    agent any

    tools {
        // Specify the configured JDK tool name in Jenkins
        jdk 'jdk'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                // Use npm ci for better consistency with package-lock.json
                sh 'npm ci'
            }
        }

        stage('Backend') {
            steps {
                // Use a cleaner way to change directories within a stage
                dir('app/backend') {
                    sh 'npm ci'
                }
            }
        }

        stage('Frontend') {
            steps {
                // Use a cleaner way to change directories within a stage
                dir('app/frontend') {
                    sh 'npm ci'
                }
            }
        }

        stage('Deploy to Container') {
            steps {
                // Consider using npm scripts or custom scripts for deployment
                sh 'npm run compose:up -d'
            }
        }
    }
}
