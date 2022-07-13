pipeline {
    agent any

    stages {
        stage ("cleanup") {
            steps {
                cleanWs()
                checkout scm
            }
        }
        stage ("test") {
            when {
                expression {
                    BRANCH_NAME = 'master' || BRANCH_NAME = 'dev'
                }
            }
            steps {
                echo 'Test phase can be executed here'
            }
        }
        stage('Build') {
            steps {
                rtGradleRun (
                    usesPlugin: true, // Set to true if the Artifactory Plugin is already defined in build script
                    useWrapper: true,
                    tasks: 'clean build',
                    switches: '--info --refresh-dependencies'
                )
            }
        }
    }
}
