node {
   def mvnHome
   stage('Build') {
      cleanWs()
      git 'https://github.com/sureshmurthy85/minecraft-ios.git'
      mvnHome = tool 'mvn'
      withEnv(["MVN_HOME=$mvnHome"]) {
          sh '"$MVN_HOME" install'
      }
   }
   stage('Test') {
       archiveArtifacts 'target/*.jar'
       junit 'target/surefire-reports/*.xml'
   }   
   stage('Publish'){
        cloudBeesFlowCallRestApi body: '', configuration: 'flow-server', envVarNameForResult: '', httpMethod: 'DELETE', urlPath: '/artifacts/com.demo:helloworld'
	      cloudBeesFlowPublishArtifact artifactName: 'com.demo:helloworld', artifactVersion: 'release-1.0-SNAPSHOT', configuration: 'flow-server', filePath: 'target/helloworld-1.0-SNAPSHOT.jar', repositoryName: 'default'
   }
   stage('Results') {
       cloudBeesFlowRunPipeline addParam: '{"pipeline":{"pipelineName":"Deploy Pipeline","parameters":[]}}', configuration: 'flow-server', pipelineName: 'Test Pipeline', projectName: 'Test'    
   }
}
