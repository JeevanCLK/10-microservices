pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "cd /var/lib/jenkins/workspace/plication_to_AWS_EKS_cartservice/src"
                        sh "docker build -t jeevanclk/cart-service:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push jeevanclk/cart-service:latest "
                    }
                }
            }
        }
    }}


