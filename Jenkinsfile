pipeline{
    agent any
    environment {
        PATH = "/opt/maven/apache-maven-3.8.1/bin:$PATH"
    }
    stages {
        stage("Clone Code"){
            steps{
                git branch: 'main', credentialsId: '97f5c5f5-8fdf-46b8-97ff-8a4dc77ac078', url: 'https://github.com/abhilash-1324/User-Registration.git'
            }
        }
        stage("Build code"){
            steps{
                sh "mvn clean install"
            }
        }
    }
}
