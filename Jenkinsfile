pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository...'
                // SCM checkout already happens automatically
            }
        }
        stage('Check Python and Pip') {
            steps {
                echo 'Checking Python and pip installation...'
                bat '''
                    python --version
                    if %ERRORLEVEL% NEQ 0 (
                        echo Python is NOT installed. Please install Python and add it to PATH.
                        exit /b 1
                    )
                    pip --version
                    if %ERRORLEVEL% NEQ 0 (
                        echo Pip is NOT installed. Please install pip and add it to PATH.
                        exit /b 1
                    )
                '''
            }
        }
        stage('Install dependencies') {
            steps {
                echo 'Installing Python dependencies...'
                bat 'python -m pip install -r requirements.txt'
            }
        }
        stage('Run application') {
            steps {
                echo 'Running the application...'
                bat 'weather_app.py' // Change this to your actual run command
            }
        }
    }
}
