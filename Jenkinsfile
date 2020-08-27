node()
{
properties([
   parameters([
    string(name: 'status', defaultValue: 'SUCCESS')
    ])
   ])
  stage("Stage1")
  {
      // something went wrong, but it isn't catastrophic...
	  currentBuild.result = 'SUCCESS'
  }
}
