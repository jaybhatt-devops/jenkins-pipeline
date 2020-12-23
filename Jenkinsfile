pipeline {
    agent any

    stages {
        stage('Updating') {
            steps {
                echo 'Updating'
        //        sh 'apt-get update'
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
            environment {
                server= credentials('aws')            
            }
            steps {
                echo 'Deploying to Ec2 Server'
                sh " echo 'My user name is $server_USR'"
                sh " echo 'My pass is $server_PSW'" //Private Key
          //      withCredentials([sshUserPrivateKey(credentialsId: 'AWSCred', keyFileVariable: 'newkey.pem', passphraseVariable: '', usernameVariable: 'username')]) {
          //          sh 'ssh -i key user@65.0.102.44'
          //          sh 'ls -la'
          //          echo "Connected > user.txt"
 // }                                                                                                      
            }
        }
    }
}
