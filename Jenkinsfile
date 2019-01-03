pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000 -p 5000:5000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                HTTPS_PROXY = 'http://httppxgot.srv.volvo.com:8080'
                HTTP_PROXY = 'http://httppxgot.srv.volvo.com:8080' 
                PROXY_ENABLED = 'TRUE' 
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
