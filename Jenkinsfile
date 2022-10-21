pipeline {
    agent any
    stages {
        stage("Build Docker Image") {
            steps {
                scrip {
                    dockerapp = docker.build("dtoulouzas/kube-news:${env.BUILD_ID}", '-f ./src/dockerfile ./src')
                }
            }
        }
    }
}