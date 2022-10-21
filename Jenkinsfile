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
    }
    stage ('Push docker image') {
        steps{
            script {
                docker.withRegistry('https://resgistry.hub.docker.com', 'dockerhub')
                    dockerapp.push('latest')
                    dockerapp.push("${env.BUILD_ID}")
            }

        }
    }
}