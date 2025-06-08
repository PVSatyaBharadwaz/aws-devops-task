
pipeline {
    agent any
      stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build Application') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy to S3') {
            steps {
                withCredentials([aws(credentials: 'aws-credentials-s3')]) {
                    sh "aws s3 sync dist/ s3://aws-devops-task-satyab --delete"
                }
            }
        }
    }
}
