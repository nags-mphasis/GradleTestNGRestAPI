pipeline {

    agent any

    stages {
        stage('build') {
            steps {
                sh './gradlew clean'
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
        stage('Test Reports') {
            steps {
                publishHTML (target: [
                allowMissing: false,
                alwaysLinkToLastBuild: false,
                keepAll: true,
                reportDir: 'build/reports/tests/test',
                reportFiles: 'index.html',
                reportName: "TestNG Report"
                ])
            }
        }
    }
    
    post {
        unsuccessful {
            cleanWs()
        }
    }
}
