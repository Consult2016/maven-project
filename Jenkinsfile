pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh '/home/consult2016/Development/artifacts/apache-maven-3.6.0/bin/mvn clean package'
            }
            post {
              success {
                echo 'Now Archiving...'
                archiveArtifacts artifacts: '**/target/*.war'
              }
            }
          }
        stage ('Deploy To Staging'){
          steps {
            build job: 'ascdso-deploy-prod'
          }
        }
      }
  }
