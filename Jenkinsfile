pipeline {
    agent any
    
    tools {
        jdk 'jdk' // Use 'jdk' instead of 'jdk17'
        
    }
    stages {
        stage('Git Checkout') {
            steps {
                git credentialsId: 'git-token', url: 'https://github.com/Rakeshkumar9900/banking-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh "npm install"
            }
        }

        stage('Backend') {
            steps {
                dir('/root/.jenkins/workspace/Bank/app/backend') {
                    sh "npm install"
                }
            }
        }

        stage('frontend') {
            steps {
                dir('/root/.jenkins/workspace/Bank/app/frontend') {
                    sh "npm install"
                }
            }
        }

        stage('Deploy to Container') {
            steps {
                sh "npm run compose:up -d"
            }
        }
    }
}
