 stage('Build') {
      cleanWs()
      git 'https://github.com/sureshmurthy85/forrester_demo_2020.git'
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
	    cloudBeesFlowPublishArtifact artifactName: 'com.demo:helloworld', artifactVersion: 'release-2.0-${BUILD_NUMBER}-SNAPSHOT', configuration: 'flow-server-latest', filePath: 'target/helloworld-1.0-SNAPSHOT.jar', repositoryName: 'default'
   }
   stage('Run Flow Pipeline'){
       cloudBeesFlowRunPipeline addParam: '{"pipeline":{"pipelineName":"Test Pipeline","parameters":[]}}', configuration: 'flow-server-latest', pipelineName: 'Test Pipeline', projectName: 'Test'
   }
