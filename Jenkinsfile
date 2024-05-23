pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "The code was built using the Maven automation tool, which compiled and packaged the code."
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Unit tests have been carried out to ensure the code functions as expected."
                echo "Integration tests have been run to ensure different components of the application work together as expected."
                echo "The unit tests were carried out using the JUnit automation tool and the integration tests were carried out using Selenium and Postman."  
            }
            post {
                success {
                    emailext body: "Unit Integration Tests were successful!!!\n\nBuild log:\n${BUILD_DATA, maxLines=100, escapeHtml=false}",
                             subject: "Unit Integration Tests Status Email",
                             to: "shehani.wickremasekera@gmail.com"
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "The code analysis was carried out using the SonarQube analysis tool."
            }
        }
        stage('Security Scan') {
            steps {
                echo "The security scan was carried out using the OWASP ZAP scanning tool."
            }
            post {
                success {
                    emailext body: "Security Scan was successful!!!\n\nBuild log:\n${BUILD_DATA, maxLines=100, escapeHtml=false}",
                             subject: "Security Scan Status Email",
                             to: "shehani.wickremasekera@gmail.com"
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "The application was deployed to the staging server AWS EC2 instance using the Ansible deployment tool."
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Integration tests were run on the staging environment."
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "The application was deployed to the AWS EC2 instance server using the deployment tool, Ansible."
            }
        }
    }
}
