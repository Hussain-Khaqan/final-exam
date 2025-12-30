pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Source code cloned automatically from GitHub by Jenkins'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                python --version
                python -m venv venv
                venv\\Scripts\\pip install --upgrade pip
                venv\\Scripts\\pip install -r requirements.txt
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat '''
                venv\\Scripts\\pytest
                '''
            }
        }

        stage('Build Application') {
            steps {
                bat '''
                if not exist build mkdir build
                copy app.py build\\
                copy requirements.txt build\\
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deployment simulated successfully (Flask app ready)'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully'
        }
        failure {
            echo 'CI/CD Pipeline failed'
        }
    }
}
