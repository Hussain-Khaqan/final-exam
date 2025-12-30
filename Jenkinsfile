pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                // Clones the GitHub repo into Jenkins workspace
                git branch: 'main', url: 'https://github.com/Hussain-Khaqan/final-exam.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Using system Python and installed dependencies
                bat """
                REM Check Python version
                python --version

                REM Upgrade pip just in case
                python -m pip install --upgrade pip

                REM Ensure required packages are installed
                python -m pip install -r requirements.txt
                """
            }
        }

        stage('Run Unit Tests') {
            steps {
                bat """
                REM Run pytest on all test files
                pytest
                """
            }
        }

        stage('Build Application') {
            steps {
                bat """
                REM Create build directory if it does not exist
                if not exist build mkdir build

                REM Copy Flask app and requirements for deployment
                copy app.py build\\
                copy requirements.txt build\\
                """
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deployment simulated: Flask app is ready in the build folder.'
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
