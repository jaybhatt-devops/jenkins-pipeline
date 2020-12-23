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
                withCredentials([usernameColonPassword(credentialsId: 'AWSCred', variable: 'USERPASS')]) {
                    sh 'ls -la'
                    sh 'echo "$USERPASS" > pass.txt' 
    
  }                                                                                                      
            }
        }
}
