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
                sh "docker build -t phairotana/htmlqrcode:latest ."
            }
        }
        stage('Push Docker to Registry') {
            steps {
                echo "Step 3: Push image to registry ..."
                withCredentials([usernamePassword(credentialsId: 'MyCredential_ID', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
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
                echo "Step 4: Starting deployment script ..."
                // sh 'ssh root@172.31.26.159 /opt/mydeployment/deploy.sh'
            }
        }
    }
}
