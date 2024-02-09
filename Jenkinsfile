pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                echo 'Params: ${params.Flavor}'
            }
        }
        stage('Compile') {
            steps {
                script {
                    'gradlew clean compileDebugSources'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    'gradlew clean assembleDebug'
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