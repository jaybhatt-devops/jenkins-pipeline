pipeline {
    agent any

    stages {
        stage('Updating') {
            steps {
                echo 'Updating'
                sh 'apt-get update'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
