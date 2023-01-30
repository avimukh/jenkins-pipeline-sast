pipeline{
	agent any
	tools {
        go 'myGoLang'
    }
	environment {
        GO119MODULE = 'on'
        CGO_ENABLED = 0 
        GOPATH = "${JENKINS_HOME}/workspace/${JOB_NAME}"
		//GOROOT = "${JENKINS_HOME}/workspace/${JOB_NAME}/workspace"
		goHome = tool 'myGoLang'
		PATH = "$goHome/bin:$PATH"
    }
	stages{
		stage('CloneRepo'){
			steps{
				script{
						sh "rm -r ./sast-to-ast-export"
						sh "git clone https://github.com/Checkmarx/sast-to-ast-export.git"
						sh "pwd"
						//sh "printenv"
						//sh "rm -r $goHome/src/"
						//sh "cp -f -R ./sast-to-ast-export/ ."
						//sh "ls -lart $goHome/src/sast-to-ast-export"
						//sh "go version"
						sh "ls -lart ./sast-to-ast-export"
						//sh "rm go.mod"
						sh "mkdir -p $goHome/src"
						sh "ln -s $goHome/src ./sast-to-ast-export"
					}
			}
		}
		stage('Build'){
			
			steps{
					dir('sast-to-ast-export'){
					//cmd_exec(cd /sast-to-ast-export)
					//cmd_exec(go build)
					//sh 'go get -u golang.org/x/lint/golint'
					sh "go version"
					sh "pwd"
					//sh "rm go.mod"
					//sh "go mod init github.com/checkmarxDev/ast-sast-export"
					//sh "go mod tidy"
					//Ssh "go get github.com/checkmarxDev/ast-sast-export"
					sh "go build"
					}
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
