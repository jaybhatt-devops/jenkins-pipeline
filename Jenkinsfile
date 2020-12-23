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
                sh 'mvn clean --file my-app/pom.xml'
                echo 'Build started on `date`'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing'
                sh 'mvn test -f my-app/pom.xml'
            }
        }
        
        stage('Packaging') {
            steps {
                echo 'Packaging'
                sh 'mvn package -f my-app/pom.xml'
                sh 'cp my-app/target/*.jar .'
                sh 'ls -la'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying to Ec2 Server'
                withCredentials([sshUserPrivateKey(credentialsId: 'AWSCred', keyFileVariable: 'Key', usernameVariable: 'User')]) {
                    sh 'ssh -i key User@65.0.102.44'
                    sh 'ls -la'
                    echo "Connected > user.txt"
  }                                                                                                      
            }
        }
    }
}
