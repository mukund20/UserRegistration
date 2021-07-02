pipeline{
    agent any
    environment {
        PATH = "/opt/maven/apache-maven-3.8.1/bin:$PATH"
    }
    stages{
        
        stage("Clone Code"){
            steps{
                git branch: 'main', credentialsId: '97f5c5f5-8fdf-46b8-97ff-8a4dc77ac078', url: 'https://github.com/abhilash-1324/UserRegistration.git'
            }
        }
        
        stage("Build Code"){
            steps{
                sh "mvn clean package"
            }
            post {
                success {
                    echo "Archiving artifacts..."
                    archiveArtifacts artifacts: '**/target/*.war', fingerprint: true 
            }
        }
        }     
        stage("Test Code"){
            steps{
                sh "mvn test"
            }
        }
        
        stage("Deploy code"){
            steps{
                sshagent(['deploy_user']){
                sh "scp -o StrictHostKeyChecking=no target/*.war  ec2-user@3.20.238.206:/opt/apache-tomcat-9.0.48/webapps"
                }
            }
        }
    }
}
