pipeline {
    agent any

    stages {
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
