pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Hussain-Khaqan/final-exam.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                sh '''
                . venv/bin/activate
                pytest
                '''
            }
        }

        stage('Build Application') {
            steps {
                sh '''
                echo "Preparing application for deployment..."
                tar -czf flask_app.tar.gz app.py requirements.txt
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                echo "Simulating deployment..."
                echo "Application deployed successfully!"
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully 🎉'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
    }
}
