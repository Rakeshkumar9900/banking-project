pipeline {
    agent any
    
    tools{
        jdk 'jdk17'
        nodejs 'node16'
    
    
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
        
        stage('Deploy to Conatiner') {
            steps {
                sh "npm run compose:up -d"
            }
        }
    }
}
