pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Cette étape permet de récupérer ton code source depuis le dépôt Git
                git 'https://github.com/maramnaili/devops-tp.git'
            }
        }
        // Autres étapes (build, tests, déploiement, etc.)
        stage('Build Docker') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE} .'
            }
        }
        stage('Post-Deployment Validation') {
            steps {
                script {
                    // Smoke test
                    sh 'curl http://localhost:5000 && echo "App is up!"'
                }
            }
        }
        stage('Push Docker') {
            steps {
                sh 'echo "docker push ${DOCKER_IMAGE}"'
            }
        }
    }
}
