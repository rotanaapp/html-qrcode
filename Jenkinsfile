pipeline {
    agent any
    stages {
        stage('Deploy html site') {
            steps {
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'index.html', reportName: 'HTML QR CODE', reportTitles: '', useWrapperFileDirectly: true])
            }
        }
        stage('Build Docker Image') {
            steps {
                echo "Starting docker build..."
                sh "docker build -t phairotana/htmlqrcode:latest ."
            }
        }
        stage('Push Docker to Registry') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerRegistryCredential', myusername: 'DOCKER_USERNAME', mypassword: 'DOCKER_PASSWORD')]) {
                    sh '''
                        echo "Logging into Docker registry..."
                        docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD
                        echo "Pushing Docker image to registry..."
                        docker push phairotana/htmlqrcode:latest
                    '''
                }
            }
        }
        stage('Execute deployment script') {
            steps {
                echo "Starting deployment script execution..."
                sh 'ssh root@172.31.26.159 /opt/mydeployment/deploy.sh'
            }
        }
    }
}
