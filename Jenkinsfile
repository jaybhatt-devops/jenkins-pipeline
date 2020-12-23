pipeline {
    agent any

    stages {
        stage('Updating') {
            steps {
                echo 'Updating'
                sh 'apt-get update'
            }
        }
        stage('Build') {
            steps {
                echo 'Building'
                sh 'ls -la'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
