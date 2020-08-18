node {
   def mvnHome  
   properties([
   parameters([
    string(name: 'myParam', defaultValue: '')
    ])
   ])
   stage('Build') {
      cleanWs()
      git 'https://github.com/sureshmurthy85/minecraft-ios.git'
      mvnHome = tool 'mvn'
      withEnv(["MVN_HOME=$mvnHome"]) {
          sh '"$MVN_HOME/bin/mvn" install'
      }
   }
   stage('Test') {
       archiveArtifacts 'target/*.jar'
       junit 'target/surefire-reports/*.xml'
   }   
   stage('Publish'){
	    cloudBeesFlowPublishArtifact artifactName: 'com.demo:minecraft-ios', artifactVersion: 'release-1.0-${BUILD_NUMBER}-SNAPSHOT', configuration: 'flow-server-latest', filePath: 'target/minecraft-ios-1.0-SNAPSHOT.jar', repositoryName: 'default'
   }
   stage('Run Flow Pipeline'){
       cloudBeesFlowRunPipeline addParam: '{"pipeline":{"pipelineName":"Test Pipeline","parameters":[]}}', configuration: 'flow-server-latest', pipelineName: 'Test Pipeline', projectName: 'Test'
   }
}
