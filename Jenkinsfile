pipeline {
    agent any

    environment {
        // Optional: Set if Jenkins service PATH does not include Python
        // PYTHON_PATH = "C:\\Users\\Hussain\\AppData\\Local\\Programs\\Python\\Python310\\python.exe"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Hussain-Khaqan/final-exam.git'
                echo 'Repository cloned successfully from GitHub'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Skipping install: Python and dependencies already installed system-wide'
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat '''
                REM Run pytest using system Python
                pytest
                '''
            }
        }

        stage('Build Application') {
            steps {
                bat '''
                REM Create build folder if it does not exist
                if not exist build mkdir build

                REM Copy Flask app and requirements for deployment
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
            echo 'CI/CD Pipeline completed successfully 🎉'
        }
        failure {
            echo 'CI/CD Pipeline failed ❌'
        }
    }
}
