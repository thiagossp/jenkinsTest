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
                    bat 'gradlew clean assembleDebug'
                }
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts '**/build/outputs/**/*.apk'
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