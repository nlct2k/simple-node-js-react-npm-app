pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git branch: 'main', url:'https://github.com/nlct2k/simple-node-js-react-npm-app.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
