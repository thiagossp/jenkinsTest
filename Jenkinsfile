pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Build') {
            steps {
                script {
                    sh './gradlew compileDebugSources'
                }
            }
        }
        stage('Approval') {
            steps {
                script {
                    timeout(time: 2, unit: 'MINUTES') {
                        input message: 'Aprovar?', ok: 'Sim'
                    }
                }
            }
        }
    }
}