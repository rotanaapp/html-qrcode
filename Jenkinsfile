pipeline {
    agent any
    stages {
        stage('Deploy html site') {
            steps {
                echo "Step 1: Html Publisher ..."
            }
        }
        stage('Build Docker Image') {
            steps {
                echo "Step 2: Starting docker build ..."
                script{
                    sh 'docker push phairotana/htmlqrcode:latest .'
                }
            }
        }
    }
}
