pipeline{
    agent any
    environment {
        PATH = "/opt/maven/apache-maven-3.8.3/bin:$PATH"
    }
    stages{
        
        stage("Clone Code"){
            steps{
                git branch: 'main', url: 'https://github.com/mukund20/UserRegistration.git'
            }
        }
        
        stage("Build Code"){
            steps{
                sh "mvn clean package"
            }
        }     
        
        stage("Test Code"){
            steps{
                sh "mvn test"
            }
        }
        
        stage("Deploy code"){
            steps{
                sshagent(['2d99a64e-3ece-4ecb-87b6-95c065cca6b3']) {
                sh "scp -o StrictHostKeyChecking=no target/*.war  ubuntu@3.108.59.136/:/opt/apache-tomcat-9.0.48/webapps"
                }
            }
        }
    }
}
