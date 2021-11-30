pipeline {
    agent any
	environment {
        PATH = "$PATH:/opt/apache-maven-3.6.3/bin"
    }
    stages{
        stage('Get Code'){
            steps{
                git 'https://github.com/RatiRanjanDas/hello-world.git'
            }
         }
		stage('Build Code'){
            steps{
                 sh 'mvn clean install'
            }
        }
        stage('Deploy'){
            steps{
			  sshagent(['tomcat_login']) {
			     sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@13.233.56.243:/opt/apache-tomcat/webapps"
                }
            }
        }
    }
}
