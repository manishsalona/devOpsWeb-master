pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
  stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deployments'){
            parallel{
                stage ("Deploy to Staging"){
                    steps {
                        deploy adapters: [tomcat9(credentialsId: 'd8f620d5-7173-4ca2-af8e-394ed222b62a', path: '', url: 'http://127.0.0.1:8082/')], contextPath: 'devOpsWeb-master', war: '**/*.war'
                    }
                }
            }
         }
       }            
}
