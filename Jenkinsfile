pipeline{
    parameters {
         booleanParam defaultValue: true, name: 'sonar'
         choice choices: ['dev', 'qa', 'uat', 'pre-produ', 'production'], name: 'env'
         string defaultValue: 'ls -l', name: 'command'
         text defaultValue: '''dadad
         adada
         adad''', name: 'text'
         }

	agent {label 'dev'}
	stages {
		stage('GIT checkout') {
			steps {
				checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/OpqTech/java-onlinebookstore.git']])
			}
		}
		stage('Build') {
			steps {
				echo 'This is Build stage'
			}
		}
		stage('Push') {
			steps {
				echo 'This is push stage'
			}
		}
		stage('Sonar Scan ') {
			steps {
				echo 'This is sonar scan stage'
			}
		}		
		stage('Deploy') {
			parallel {
				stage ('Deploy - Dev') {	
					steps {
						echo 'This is dev deployment'
						sh 'sleep 10'
					}
				}
				stage ('Deploy - Qa') {	
					steps {
						echo 'This is Qa deployment'
						sh 'sleep 10'
					}
				}
				stage ('Deploy - UAT') {	
					steps {
						echo 'This is uat deployment'
						sh 'sleep 10'
					}
				}
			}				
		}
	}
}
