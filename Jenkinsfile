pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Using Gradle for automated builds" // Changed Maven to Gradle
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit and integration tests with TestNG" // Changed JUnit to TestNG
            }
		post {
                success {
                    emailext attachLog: true,
                    subject: "Tests Completed Successfully",
		    body: "Unit and Integration Tests are completed successfully.",
                    to: "shehani.wickremasekera@gmail.com"  
                }
                failure {
                    emailext attachLog: true,
                    subject: "Tests Failed",
		    body: "Unit and Integration Tests got failed. Check the logs for details.",
                    to: "shehani.wickremasekera@gmail.com" 
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Running code analysis with SonarCloud" // Changed SonarQube to SonarCloud
            }
        }
        stage('Security Scan') {
            steps {
                echo "Running security scan with Snyk" // Changed OWASP ZAP to Snyk
            }
		post {
                success {
                   	emailext attachLog: true,
			subject: 'Security Scan Completed Successfully',
			body: 'Security Scan completed successfully.',
                    	to: 'shehani.wickremasekera@gmail.com'
                }
                failure {
                        emailext attachLog: true,
                        subject: 'Security Scan Failed',
			body: 'Security Scan failed. Check the logs for details.',
                        to: 'shehani.wickremasekera@gmail.com'      
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging server AWS EC2(staging)"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging environment"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production server (AWS EC2)"
            }
        }
    }
    post {
        success {
 
           	emailext attachLog: true,
                subject: "Pipeline Successful",
                body: "The Jenkins pipeline completed successfully.",
               	to: "shehani.wickremasekera@gmail.com"
        }
        failure {
           	emailext attachLog: true,
                subject: "Pipeline Failed",
                body: "The Jenkins pipeline failed. Check the logs for details.",
                to: "shehani.wickremasekera@gmail.com" 
        }
    }
}
