pipeline {
    agent any
       tools {
          maven 'maven'
             }
           
    stages {
        stage("clone code"){
            steps{
               git credentialsId: 'git_credentials', url: 'https://github.com/Mounika475/hello-world.git'
            }
        }
        stage("build code"){
            steps{
              sh "mvn clean install"
            }
        }
        stage("deploy"){
            steps{
              sshagent(['deploy_user']) {
                 sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@18.218.177.105:/root/apache-tomcat-8.5.57/webapps"

                 
                }
            }
        }
    }
}
