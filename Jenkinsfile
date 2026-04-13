pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'lelon761/django-polls'
        EC2_USER = 'ubuntu'
        EC2_HOST = '18.191.209.203'
        DOCKER_CREDS = 'docker-hub-credentials'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/lelon761/django-polls.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:latest")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDS) {
                        docker.image("${DOCKER_IMAGE}:latest").push()
                        echo 'Docker image pushed successfully.'
                    }
                }
            }
        }

        stage('Deploy on EC2') {
            steps {
                sshagent(credentials: ['ec2-ssh-private-key']) {
                    sh """
                    ssh -o StrictHostKeyChecking=no ${EC2_USER}@${EC2_HOST} '
                        docker pull ${DOCKER_IMAGE}:latest &&
                        docker stop django-polls-container || true &&
                        docker rm django-polls-container || true &&
                        docker run -d --name django-polls-container -p 8000:8000 ${DOCKER_IMAGE}:latest &&
                        docker ps -a
                    '
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed.'
        }
    }
}
