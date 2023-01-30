pipeline{
	agent any
	stages{
		stage('CloneRepo'){
			steps{
				script{
					sh "git clone https://github.com/Checkmarx/sast-to-ast-export.git"
					sh "ls -lart ./*"
					sh "pwd"}
			}
		}
		stage('Test'){
			steps{
				
				echo "Test"
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
