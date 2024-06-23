pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your Git repository
                git 'https://github.com/Dineshappu/boxfuse.git'
            }
        }

        stage('Build') {
            steps {
                // Set up Maven environment (if needed)
                script {
                    env.MAVEN_HOME = tool 'Maven' // Make sure 'Maven' is configured in Jenkins Global Tool Configuration

                    // Clean and package the Maven project
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                 script {
            def warFilePath = '/var/lib/jenkins/workspace/warProjectPL/target/hello-1.0.war'
            def tomcatWebappsPath = '/usr/tomcat/tomcat10/webapps'
                     
            sh "sudo -S cp ${warFilePath} ${tomcatWebappsPath}"
                        // Restart Tomcat to deploy the application (if necessary)
                        sh 'sudo systemctl restart tomcat'
                    
                }
            }
        }
    }
}
