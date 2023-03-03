
pipeline {
    agent any
//     environment {
//         DOCKER_HUB_USERNAME = credentials('docker-hub-creds').username
//         DOCKER_HUB_PASSWORD = credentials('docker-hub-creds').password
//     }
    stages {
        stage('Clone Step') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/yogeshgowda07/hello-world-war.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mvn_docker .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withDockerRegistry([ credentialsId: "docker-hub-creds", url:""]) {
                    sh 'docker tag mvn_docker yogesh6520/mvn_docker:$BUILD_NUMBER'
                    sh 'docker push yogesh6520/mvn_docker:$BUILD_NUMBER' 
                }
            }
        }
        stage('Deploy Step') {
            steps {
                sh 'docker rm -f tom_docker'
                sh 'docker run -itd -p 8070:8080 --name tom_docker mvn_docker'
            }
        }
    }
}
