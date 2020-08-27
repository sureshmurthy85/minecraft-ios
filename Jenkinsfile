node()
{
properties([
   parameters([
    string(name: 'ABORTED', defaultValue: 'SUCCESS')
    ])
   ])
  stage("Stage1")
  {
      // something went wrong, but it isn't catastrophic...
	  currentBuild.result = "${ABORTED}"
  }
}
