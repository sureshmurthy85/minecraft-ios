pipeline {
    agent any
    parameters {
        string(name: 'ABORTED defaultValue: 'SUCCESS')
    }
    stages {
        stage('Dev') {
            steps {
                echo "${params.ABORTED}"
            }
        }
    }
}
