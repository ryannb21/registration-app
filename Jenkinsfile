pipeline {
    agent any

    stages {
        stage('Continuous Download') {
            steps {
                echo 'DOWNLOADING IN PROGRESS...'
                git branch: 'main', url: 'https://github.com/chamberlain96/registration-app.git'
            }
        }
        stage('Continuous Build') {
            steps {
                echo 'BUILDING IN PROGRESS...'
                sh 'mvn clean install'
            }
        }
        stage('Approval") {
              steps {
                  input message: 'Proceed to Deployment?', ok: 'Approve'
              }
        }
        stage('Continuous Delivery') {
            steps {
                echo 'DELIVERY IN PROGRESS...'
                deploy adapters: [tomcat9(credentialsId: 'tomcat10', path: '', url: 'http://54.159.133.100:8080/')], contextPath: 'ryanapp4', war: '**/*war'
            }
        }
    }
}
