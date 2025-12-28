pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/<username>/python-ci-cd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t <dockerhub-username>/python-app:latest .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push <dockerhub-username>/python-app:latest'
            }
        }

        stage('Deploy Using Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml'
            }
        }
    }
}
