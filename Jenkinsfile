pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK21'
    }

    stages {

        stage('Build') {
            steps {
				
                bat 'mvn clean compile'
            }
        }

        stage('Test Execution') {
            steps {
                bat 'mvn test'
            }
        }
    }

    post {
		always {
			publishHTML([
				allowMissing : true,
				alwaysLinkToLastBuild : true,
				keepAll:true,
				reportDir : 'test-output',
				reportFiles: 'emailable-report.html',
				reportName:'TestNG Report'
			
			])
		}

        success {
            echo 'BUILD SUCCESSFUL'
        }

        failure {
            echo 'BUILD FAILED'
        }

        always {
            echo 'PIPELINE COMPLETED'
        }
    }
}