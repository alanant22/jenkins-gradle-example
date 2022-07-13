pipeline {
    agent any

    stages {
        stage ("cleanup") {
            steps {
                cleanWs()
                checkout scm
                echo env.BRANCH_NAME
            }
        }
        stage ("test") {
            when {
                expression {
                    env.BRANCH_NAME == 'master' || env.BRANCH_NAME == 'dev'
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
