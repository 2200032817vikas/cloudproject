pipeline {
    agent any

    environment {
        PYTHON_HOME = 'C:\\Users\\mvssns prasadrao\\AppData\\Local\\Programs\\Python\\Python313'
    }

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository...'
                // SCM checkout happens automatically
            }
        }

        stage('Check Python and Pip') {
            steps {
                echo 'Checking Python and pip installation...'
                bat '''
                    "%PYTHON_HOME%\\python.exe" --version
                    if %ERRORLEVEL% NEQ 0 (
                        echo Python is NOT found at %PYTHON_HOME%.
                        exit /b 1
                    )
                    "%PYTHON_HOME%\\Scripts\\pip.exe" --version
                    if %ERRORLEVEL% NEQ 0 (
                        echo Pip is NOT found at %PYTHON_HOME%.
                        exit /b 1
                    )
                '''
            }
        }

        stage('Install dependencies') {
            steps {
                echo 'Installing Python dependencies...'
                bat '"%PYTHON_HOME%\\Scripts\\pip.exe" install -r requirements.txt'
            }
        }

        stage('Run application') {
            steps {
                echo 'Running the application...'
                bat '"%PYTHON_HOME%\\python.exe" weather_app.py'
            }
        }
    }
}
