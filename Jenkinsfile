pipeline{
    agent any
    
    stages{
        
        stage("Clone Code"){
            steps{
                git branch: 'main', url: 'https://github.com/abhilash-1324/UserRegistration.git'
            }
        }
        
        stage("Build Code"){
            steps{
                sh "mvn clean package"
            }
            post {
                success {
                    echo "Archiving artifacts..."
                    archiveArtifacts artifacts: '**/target/*.war'
            }
        }
        }     
        stage("Test Code"){
            steps{
                sh "mvn test"
            }
        }
        
    }
}
