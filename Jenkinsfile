pipeline {
    agent any
    environment {
        PATH = "/usr/tomcat/tomcat10/webapps:$PATH"
    }
    stages {
        stage('Build code') {
            steps {
                dir('/home/ec2-user/workspace/warProjectPL') {
                    sh 'mvn clean install'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'cp /home/ec2-user/workspace/warProjectPL/target/hello-1.0.war /usr/tomcat/tomcat10/webapps'
            }
        }
    }
}
