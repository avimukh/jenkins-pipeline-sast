pipeline{
	agent any
	stages{
		stage('CloneRepo'){
			steps{
				script{
					sh "git clone https://github.com/Checkmarx/sast-to-ast-export.git"
					sh "ls -lart ./sast-to-ast-export"
					sh "pwd"}
			}
		}
		stage('RunUtility'){
			steps{
				cmd_exec(.\sast-to-ast-export\cxsast_exporter --user username --pass password --url http://localhost)
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
