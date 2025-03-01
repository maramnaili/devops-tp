pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "maramnaili/hello-devops"
    }
    stages {
        // Étape de construction de l'image Docker
        stage('Build Docker') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE} .'
            }
        }

        // Étape de validation post-déploiement (test de validation avec curl)
        stage('Post-Deployment Validation') {
            steps {
                script {
                    // Smoke test: envoi une requête curl à l'application
                    sh 'curl http://localhost:5000 && echo "App is up!"'
                }
            }
        }

        // Étape de push de l'image Docker (simulée)
        stage('Push Docker') {
            steps {
                sh 'echo "docker push ${DOCKER_IMAGE}"'
            }
        }
    }
}
