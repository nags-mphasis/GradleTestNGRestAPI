pipeline {

    agent any

    stages {
        stage('build') {
            steps {
                sh './gradlew clean build'
            }
        }
/*        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        } */
        stage('Test') {
            steps {
                sh './gradlew clean test -DsuiteXmlFile=testng.xml '
            }
        }
/*        stage('Test Reports') {
            steps {
                publishHTML (target: [
                allowMissing: false,
                alwaysLinkToLastBuild: false,
                keepAll: true,
                reportDir: 'target/HTMLReports',
                reportFiles: 'Reports.html',
                reportName: "Cucumber Report"
                ])
            }
        } */
    }
    
    post {
        unsuccessful {
            cleanWs()
        }
    }
}
