pipeline {
    agent {
        label 'slavenode'
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your Git repository
                git 'https://github.com/Dineshappu/boxfuse.git'
            }
        }


        stage('Build') {
            steps {
                sh '''
                    cd /home/ec2-user/boxfuse-sample-java-war-hello
                '''
            }
        }
        stage('Generate') {
            steps {
                sh '''
                    mvn clean install
                '''
            }
        }
}
    }
