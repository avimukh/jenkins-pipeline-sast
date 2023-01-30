pipeline{
	agent any
	environment {
        GO114MODULE = 'on'
        CGO_ENABLED = 0 
        GOPATH = "${JENKINS_HOME}/workspace/${JOB_NAME}/sast-to-ast-export"
		goHome = tool 'myGoLang'
		PATH = "$goHome/bin:$PATH"
    }
	stages{
		stage('CloneRepo'){
			steps{
				script{
					sh "rm -r ./sast-to-ast-export"
					sh "git clone https://github.com/Checkmarx/sast-to-ast-export.git"
					sh "ls -lart ./sast-to-ast-export"
					sh "pwd"
					sh "go version"}
			}
		}
		stage('Build'){
			
			steps{
				//cmd_exec(cd /sast-to-ast-export)
				//cmd_exec(go build)
				sh "go version"
				sh "go build"
			}
		}
		stage('IntegrationService'){
			steps{
				echo "IntegrationService "
			}
		}
	}
	post{
		always{
			echo "Pipeline run complete"
		}
		success{
			echo "Ran successfully"
		}
		failure{
			echo "Failed"
		}
	}

}
