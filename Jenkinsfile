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
                sh './mvnw deploy'
                slackSend channel: 'builds', message: "Build Sucessful ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>)"
            }
        }
    }
}
