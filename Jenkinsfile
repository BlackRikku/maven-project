pipeline {
    agent any

    tools {
        jdk 'localJDK'
        maven 'LocalMaven'
    }

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to Staging'){
            steps {
                build job: 'pipe-Deploy-to-staging'
            }
        }
    }
}