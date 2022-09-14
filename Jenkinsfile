pipeline {
    agent any
    stages {
        stage("Build") {
            echo 'Starting build'
            withGradle() {
                sh './gradlew clean build'
            }
        }
    }
}