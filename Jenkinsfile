pipeline {
    agent any
     tools {
        maven 'Maven' 
        }
    stages {
        stage("SCM"){
            steps{
                git 'https://github.com/reyanshm2021/spring-boot-war-example.git' 
            }
            
        }

        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcatserver', path: '', url: 'http://65.1.91.6:8080')], contextPath: '/app', war: '**/*.war'
              
            }
            
        }
        
    }
   
}
