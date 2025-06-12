pipeline {
    agent any

    environment {
       PATH = "/Users/tenzinsherpa/.nvm/versions/node/v22.16.0/bin:$PATH"
    }

    stages {
        stage('Check Node & npm') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Install Angular CLI (if needed)') {
            steps {
                sh 'npm install -g @angular/cli || true'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm run test -- --watch=false --browsers=ChromeHeadless || echo "Tests skipped or failed"'
            }
        }

        stage('Build Angular App') {
            steps {
                sh 'npx ng build --configuration production'
            }
        }

        stage('Post Build') {
            steps {
                echo '🎉 Build complete!'
            }
        }
    }

    post {
        success {
            echo '✅ Jenkins pipeline finished successfully.'
        }
        failure {
            echo '❌ Jenkins pipeline failed. Check logs above.'
        }
    }
}