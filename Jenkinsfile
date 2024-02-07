pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Compile') {
            steps {
                script {
                    'gradlew compileDebugSources'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    'gradlew assembleDebugSources'
                }
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts "**/*.apk"
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