pipeline {
    agent any
    parameters {
        string(name: 'ABORTED', defaultValue: 'SUCCESS')
    }
    stages {
        stage('Dev') {
            steps {
                script {
                    echo "=======> ${params.ABORTED}"
                    currentBuild.result = "${params.ABORTED}"
                }
            }
        }
    }
}
