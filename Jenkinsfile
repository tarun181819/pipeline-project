pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/tarun181819/pipeline-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mywebsite .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop mycontainer || true'
                sh 'docker rm mycontainer || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 80:80 --name mycontainer mywebsite'
            }
        }
    }
}