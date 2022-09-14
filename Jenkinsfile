pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                echo 'Starting build'
                withGradle() {
                    sh './gradlew clean build'
                }
            }
        }
    }
}