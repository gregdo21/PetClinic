pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat './mvnw package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Package') {
            steps {
                bat 'echo Package...'
            }
        }
        stage('Deploy') {
            steps {
                bat "echo 'Pulling...' + env.BRANCH_NAME"
            }
        }
    }
}