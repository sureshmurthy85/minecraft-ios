pipeline {
    agent any
    parameters {
        string(name: 'ABORTED', defaultValue: 'SUCCESS')
    }
    stages {
        stage('Dev') {
            steps {
                currentBuild.result = "${params.ABORTED}"
            }
        }
    }
}
