pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/varshadav2017/springboot-devops-project.git'
            }
        }

        stage('Build Application') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t springboot-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 9090:8080 springboot-app'
            }
        }
    }
}