pipeline {
    agent {
        label 'slavenode'
    }
    
    stages {
        stage('Checkout') {
            steps {
                script {
                    try {
                        // Checkout your Git repository
                        git(
                            url: 'https://github.com/Dineshappu/boxfuse.git',
                            branch: 'main',
                            credentialsId: 'credID'
                        )
                    } catch (Exception e) {
                        error "Checkout failed: ${e.message}"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    dir('/home/ec2-user/boxfuse-sample-java-war-hello') {
                        try {
                            sh 'mvn clean install'
                        } catch (Exception e) {
                            error "Build failed: ${e.message}"
                        }
                    }
                }
            }
        }
}
    }
