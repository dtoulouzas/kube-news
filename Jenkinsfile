pipeline {
    agent any
    stages {
        stage("Build Docker Image") {
            steps {
                script {
                    dockerapp = docker.build("dtoulouzas/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }
        }
        stage ("Push Docker Image") {
            steps {
                script {
                    docker.withDockerRegistry('https://registry.hub.docker.com', 'dockerhub')
                        dockerapp.pushToCloudFoundry('latest')
                        dockerapp.pushToCloudFoundry("${env.BUILD_ID}")
                }
            }
        }
    } 
}