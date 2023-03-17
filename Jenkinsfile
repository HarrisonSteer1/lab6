pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
    }
    stages {
        stage('deploy') {
            steps {
                sh 'sh Deploy.sh'
            }
        }   
        
         stage('Push') {         
            steps{                                   
                           sh "echo \$DOCKERHUB_CREDENTIALS_PSW | docker login -u \$DOCKERHUB_CREDENTIALS_USR --password-stdin"                                   
                           echo 'Login Completed'
                sh "docker tag trio-task-mysql:5.7  harrisonsteer/trio-task-mysql:5.7"
                sh "docker tag trio-task-flask-app  harrisonsteer/trio-task-flask-app"
                sh "docker push harrisonsteer/trio-task-mysql:5.7" 
                sh "docker push harrisonsteer/trio-task-flask-app"
            }           
        }
    }
}
