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

        stage('Deploy to Tomcat') {
            steps {
                script {
                    // Copy the generated WAR file to Tomcat's webapps directory
                    def tomcatDir = '/usr/tomcat/tomcat10' // Adjust path as per your Tomcat installation
                    def warFile = sh(returnStdout: true, script: 'ls target/*.war').trim()

                    // Check if the WAR file exists before copying
                    if (warFile) {
                        sh "sudo cp ${warFile} ${tomcatDir}/webapps/"

                        // Restart Tomcat to deploy the application (if necessary)
                        sh 'sudo systemctl restart tomcat'
                    } else {
                        error "No WAR file found in target directory"
                    }
                }
            }
        }
    }
}
