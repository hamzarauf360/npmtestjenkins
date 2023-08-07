pipeline{
	agent any
	tools {
		nodejs "node"
	}

	stages{
		stage('Fetch Code'){
			steps{
				git branch: 'main', url: 'https://github.com/hamzarauf360/npmtestjenkins.git'
			}
		}

		stage('Build'){
			steps{
				sh 'npm install'
				sh 'npm run build'
			}

			post{
				success{
					echo 'Code was built sucessfully!'
				}
			}
		}

		stage('Run Code'){
			steps{
				sh 'node lib/index.js'
			}
			
			post{
				success{
					echo 'Code ran sucessfully!'
				}
			}
		}

		stage('Generate aritifact'){
			steps{
				sh 'npm pack'
			}
			post{
				success {
					echo 'Artifact generated sucessfully, now publishing the artifact!'
					archiveArtifacts artifacts: '**/*.tgz'
				}
			}
		}
	}	
}