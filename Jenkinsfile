pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/varshadav2017/springboot-devops-project.git'
            }
        }

        stage('Build Application') {
            steps {
                sh '''
                chmod +x mvnw
                ./mvnw clean package
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                apt-get update
                apt-get install -y docker.io
                docker build -t springboot-app .
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f springboot-container || true
                docker run -d -p 9090:8080 --name springboot-container springboot-app
                '''
            }
        }

    }
}