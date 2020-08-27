node()
{	
  parameters {
        string(name: 'ABORTED', defaultValue: 'SUCCESSS', description: 'Build Status')
  }	
  stage("Stage1")
  {
   echo "=========>" + "${params.ABORTED}"	  
   // something went wrong, but it isn't catastrophic...
   currentBuild.result = "${params.ABORTED}"
  }
}
