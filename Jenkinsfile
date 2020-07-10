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
             sh "curl -v -u tomcat:tomcat -T /var/lib/jenkins/workspace/Maven/webapp/target/webapp.war 'http://ec2-3-17-204-182.us-east-2.compute.amazonaws.com:8080//manager/html/deploy?path=/MavenPipeline'"


                 
                
            }
        }
    }
}
