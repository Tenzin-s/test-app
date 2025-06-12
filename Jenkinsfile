pipeline {
    agent any

    tools {
        nodejs "NodeJS-22" // name must match the version installed in Jenkins
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Tenzin-s/test-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npx ng test --watch=false --browsers=ChromeHeadless'
            }
        }

        stage('Build') {
            steps {
                sh 'npx ng build --configuration production'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying your build...' 
                // You can add S3 deploy, FTP, Firebase deploy, etc.
            }
        }
    }
}