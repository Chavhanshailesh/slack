pipeline{
	agent any
	environment{
		
	}
	stages{
		stage('QA Build'){
			steps{
				echo 'inside qa'
			}
			
		}
		stage('User Input for E2E Deployment'){
			steps{
				input(
					id: 'userInput', message: 'Deployment On E2E', parameters: [
					[$class: 'BooleanParameterDefinition', defaultValue: false, description: '', name: 'Do you want to proceed for E2E deployment?']
				])
			}
		}
		stage('E2E Build'){
			steps{
				echo 'inside e2e'
			}
			
		}
	}
}