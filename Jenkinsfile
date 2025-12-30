pipeline {
    agent any

    environment {
        // Update this if Python is installed in a custom location
        PYTHON_HOME = "C:\\Python310" // replace with your Python installation folder
        PATH = "${env.PYTHON_HOME};${env.PATH}"
    }

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Cloning source code from GitHub...'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '''
                REM Check Python version
                python --version

                REM Create virtual environment
                python -m venv venv

                REM Upgrade pip inside venv
                venv\\Scripts\\pip install --upgrade pip

                REM Install required packages
                venv\\Scripts\\pip install -r requirements.txt
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat '''
                REM Run pytest inside virtual environment
                venv\\Scripts\\pytest
                '''
            }
        }

        stage('Build Application') {
            steps {
                bat '''
                REM Prepare build folder
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
            echo 'CI/CD Pipeline completed successfully 🎉'
        }
        failure {
            echo 'CI/CD Pipeline failed ❌'
        }
    }
}
