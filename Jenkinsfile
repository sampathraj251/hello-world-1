currentBuild.displayName = "Girmiti-app#"+currentBuild.number
pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage("clone code"){
            steps{
               git credentialsId: 'git_credentials', url: 'https://github.com/sampathraj251/hello-world-1.git'
            }
        }
        stage("build code"){
            steps{
              sh "mvn clean install"
            }
        }
        stage("deploy"){
            steps{
              sshagent(['tomcat-New'])  {
                 sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@13.127.81.125:/opt/tomcat/webapps"
                 
                }
            }
        }
    }
}
