pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test' 
            }
        }
         stage('Package') {
            steps {
                sh 'mvn package' 
            }
        }
         stage('Deploy') {
             when {
                 branch 'master'
             }
            steps {
                slackSend channel: 'builds', message: 'started ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)'
            }
        }
    }
}
