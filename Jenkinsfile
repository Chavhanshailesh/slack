pipeline{
	agent any
	environment{
		AUTHOR = sh script: "git show -s --pretty=\"%an <%ae>\" ${GIT_COMMIT}", returnStdout: true
		
	}
	stages{
		stage('QA Build'){
			steps{
				echo 'inside qa'
				echo "changes by ${AUTHOR}"
			}
			
		}
		stage('User Input for E2E Deployment'){
			steps{
				slackSend baseUrl: 'https://hooks.slack.com/services/',
				channel: 'test', color: 'warning',
				message: "Need Manual User Input In : ${env.JOB_NAME}  ${env.BUILD_NUMBER}",
				teamDomain: 'Persistent-Team', tokenCredentialId: 'Slack-Cerdentials',
				username: 'Shailesh'
				input(
					id: 'userInput', message: 'Deployment On E2E', parameters: [
					[$class: 'BooleanParameterDefinition', defaultValue: false, description: '', name: 'Do you want to proceed for E2E deployment?']
				])
			}
		}
		stage('E2E Build'){
			steps{
				echo 'inside e2e'
				echo "changes by ${AUTHOR}"
			}
			
		}
	}
}