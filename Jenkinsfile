pipeline {
    agent any

    environment {
        // If Python is not found, specific the full path to python.exe here
        // Example: PYTHON_EXE = "C:\\Users\\Administrator\\AppData\\Local\\Programs\\Python\\Python311\\python.exe"
        PYTHON_EXE = "python" 
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Hussain-Khaqan/final-exam.git'
                echo 'Repository cloned successfully'
            }
        }

        stage('Setup Virtual Environment') {
            steps {
                bat '''
                echo "Creating virtual environment..."
                "%PYTHON_EXE%" -m venv venv
                
                echo "Installing dependencies..."
                venv\\Scripts\\python -m pip install --upgrade pip
                venv\\Scripts\\pip install -r requirements.txt
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat '''
                echo "Running tests..."
                venv\\Scripts\\pytest
                '''
            }
        }

        stage('Build Application') {
            steps {
                bat '''
                echo "Building application..."
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
            echo 'Pipeline completed successfully 🎉'
        }
        failure {
            echo 'Pipeline failed. If "python" is not found, please update the PYTHON_EXE variable in the Jenkinsfile. ❌'
        }
    }
}
