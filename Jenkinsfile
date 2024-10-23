pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-repo-url.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    docker.build("your-dockerhub-username/your-app:${env.BUILD_ID}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials-id') {
                        docker.image("your-dockerhub-username/your-app:${env.BUILD_ID}").push()
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 8080:8080 your-dockerhub-username/your-app:${env.BUILD_ID}'
            }
        }
    }
}
