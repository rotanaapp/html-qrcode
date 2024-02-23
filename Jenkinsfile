pipeline {
    agent any
    stages {
        stage('Deploy html site') {
            steps {
                echo "Step 1: Html Publisher ..."
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'index.html', reportName: 'HTML QR CODE', reportTitles: '', useWrapperFileDirectly: true])
            }
        }
        stage('Build Docker Image') {
            steps {
                echo "Step 2: Starting docker build ..."
                sh "docker push phairotana/htmlqrcode:latest ."
            }
        }
    }
}
