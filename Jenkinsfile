pipeline {
    agent any
    
    tools {
        jdk 'jdk' // Use 'jdk' instead of 'jdk17'
        
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

