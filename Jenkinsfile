pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
               sh 'docker build -t pythonapp .'
               }
               
            }
        
          stage('Run Docker Container') {
            steps {
                sh  '''
                docker rm -f python-container || true
                docker run -d --name python-container -p 8501:8501  -t pythonapp
                '''
            }
        }
    }
}
