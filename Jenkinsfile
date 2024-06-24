pipeline {
  agent any 
  environment {
    PATH = "/usr/tomcat/tomcat10/webapps"

  }
  stages {
    stage('clone code') {
      steps {
        git credentialsID: 'git_credentials', url: 'https://github.com/Dineshappu/boxfuse.git'
      }
    }


    stage('build code') {
      steps {
        sh "mvn clean install"
      }
    }

 stage('deploy') {
      steps {
        sshagent(['deploy_user']){
          sh "scp -o StrictHostKeyChecking=no/home/ec2-user/workspace/warProjectPL/target/hello-1.0.war ec2-user@:172.31.81.156:/usr/tomcat/tomcat10/webapps"
      }
    }
    }
  }
  }
    
    
    
