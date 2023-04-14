def versionpython= ["python3.8", "python3.9"]

pipeline {
  agent none
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
    timeout(time: 60, unit:'MINUTES')
    timestamps()
  }
  stages {
    stage("install req"){
	  agent { label 'slave_d1' }
      steps{
        script{
	        versionpython.each {item ->
			    withPythonEnv("/usr/bin/${item}") {
						sh "python --version"
						sh "pip --version"
						sh "pip install -r requirements.txt"
			    }
	        }
		}
      }
    }
  }
}
