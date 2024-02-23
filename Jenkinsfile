pipeline {
    agent any
    stages {
        stage("Set deployment PARAM") {
            steps {
                script {
                    if (params.WORKSPACE == "dev") {
                        env.SERVER_IP == "172.31.26.159"
                    }else if (params.WORKSPACE == "uat") {
                        env.SERVER_IP == "34.224.31.127"
                    }else if (params.WORKSPACE == "prod") {
                        env.SERVER_IP == "172.31.29.204"
                    }
                }
            }
        }
        stage('Deploy html site') {
            steps {
                echo "Step 1: Html Publisher ..."
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
