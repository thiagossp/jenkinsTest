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
                    'gradlew compileDebugSources'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    'gradlew assembleDebug'
                }
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts "build/**/*.apk"
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