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
			  sshagent(['deploy_user']) {
			     sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@IP:/opt/apache-tomcat-8.5.55/webapps"
                }
            }
        }
    }
}
