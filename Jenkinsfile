pipeline {
    // add your slave label name
    agent { label 'slave_node'}
    tools{
        maven 'maven1'
    }
    stages {
        stage ('Checkout_SCM') {

            steps {
          	    
	     checkout scm
            }
        }

        stage ('Maven_Build') {

            steps {
               sh 'mvn clean package'
            }
        }
        
        stage ('Deploy_Tomcat') {

            steps {
	      sshagent(['tomcat']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@3.111.47.67:/opt/tomcat9/webapps"
	      }
         }
        }
        
    }
}
