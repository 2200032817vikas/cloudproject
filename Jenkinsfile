pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository...'
            }
        }
        
        stage('Install dependencies') {
            steps {
                echo 'Installing Python dependencies...'
                sh 'pip install -r requirements.txt'
            }
        }
        
        stage('Run application') {
            steps {
                echo 'Running the Weather App...'
                sh 'python weather_app.py'
            }
        }
    }
}
