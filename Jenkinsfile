/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any
        stage('Deploy html site') {
            steps {
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '', reportFiles: 'index.html', reportName: 'HTML QR CODE', reportTitles: '', useWrapperFileDirectly: true])
            }
    }
}
