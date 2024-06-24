pipeline {
    agent any
    environment {
        PATH = "/usr/tomcat/tomcat10/webapps:$PATH"
    }
    stages {
        stage('Clone code') {
            steps {
                git credentialsId: 'credID', url: 'https://github.com/Dineshappu/boxfuse.git'
            }
        }
        stage('Build code') {
            steps {
                dir('boxfuse-sample-java-war-hello') {
                    sh 'mvn clean install'
                }
            }
        }
        stage('Deploy') {
            steps {
                sshagent(['deploy_user']) {
                    sh 'scp -o StrictHostKeyChecking=no target/hello-1.0.war ec2-user@172.31.81.156:/usr/tomcat/tomcat10/webapps'
                }
            }
        }
    }
}
