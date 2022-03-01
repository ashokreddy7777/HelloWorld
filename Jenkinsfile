pipeline {
    agent any
    tools{
    maven 'maven'
    }
    stages {
        stage('build') {
            steps { 
                sh """
                mvn -version
                mvn clean package
                """
            }
        }
        stage('deploy') {
            steps {
                sh """
                sudo docker image build -t f9app:1.0.0 .
                sudo docker container run -d --name f9app -p 80:8080 f9app:1.0.0
                """
            }   
        }
    }
}