pipeline {
    agent {
        docker {
            image 'python:3.10'
            args '-u root'
        }
    }

    stages {

        stage('Install Requirements') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Train Model') {
            steps {
                sh 'python train.py'
            }
        }

        stage('Evaluate Model') {
            steps {
                sh 'python evaluate.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-servere/mlops-model .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push jenkins-server/mlops-model'
            }
        }
    }
}
