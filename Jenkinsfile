pipeline {
    agent any
    
    tools {
        MAVEN 'MAVEN'
    }
    parameters {
         string(name: 'localhost', defaultValue: '127.0.0.1:8082', description: 'Local Server')
    }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        
    }
}
