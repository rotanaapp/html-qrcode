pipeline {
    agent any
    stages {
        stage("Set deployment PARAM") {
            steps {
                script {
                    if (params.WORKSPACE == "dev") {
                        env.SERVER_IP == "54.159.29.52"
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
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'index.html', reportName: 'HTML QR CODE', reportTitles: '', useWrapperFileDirectly: true])
            }
        }
    }
}
