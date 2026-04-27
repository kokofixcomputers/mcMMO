pipeline {
	agent any

	tools {
		//jdk 'jdk17'
		// If you configured Maven as a Jenkins tool, add:
		maven 'Maven3'
	}

	options {
		timestamps()
		disableConcurrentBuilds()
	}

	stages {
		stage('Checkout') {
			steps {
				checkout scm
			}
		}

		stage('Build') {
			steps {
				bat 'mvn -V -B clean package -DskipTests'
			}
		}
	}

	post {
		success {
			archiveArtifacts artifacts: 'target/mcMMO.jar', fingerprint: true
		}
	}
}
