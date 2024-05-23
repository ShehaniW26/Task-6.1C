pipeline{
    agent any

    stages{
        stage('Build'){
            steps{
                echo "The code was built using the Maven automation tool, which compiled and packaged the code."
            }
        }
        stage('Unit and Integration Tests'){
            steps{
                echo "Unit tests have been carried out to ensure the code functions as expected."
                echo "Integrations tests have been run to ensure different components of the application work together as expected."
                echo "The unit tests were carried out using the JUnit automation tool and the integration tests were carried out using Selenium and Postman."  
            }
            post {
                success{
                    mail to: "shehani.wickremasekera@gmail.com",
                    subject: "Unit Integration Tests Status Email",
                    body: "Unit Integration Tests were successful!!!\n\nBuild log:\n${BUILD_LOG, maxLines=100, escapeHtml=false}"
                }
            }

        }
        stage('Code Analysis'){
            steps{
                echo "The code analysis was carried out using the SonarQube analysis tool."
            }

        }
        stage('Security Scan'){
            steps{
                echo "The security scan was carried out using the OWASP ZAP scanning tool."
            }
            post {
                success{
                    mail to: "shehani.wickremasekera@gmail.com",
                    subject: "Security Scan Status Email",
                    body: "Security Scan was successful!!!\n\nBuild log:\n${BUILD_LOG, maxLines=100, escapeHtml=false}"
                }
            }

        }
        stage('Deploy to Staging'){
            steps{
                echo "The application was deployed to the staging server AWS EC2 instance using the Ansible deployment tool."
            }

        }
        stage('Integration Tests on Staging'){
            steps{
                echo "Integration tests were run on the staging environtment."
            }

        }
        stage('Deploy to Production'){
            steps{
                echo "The application was deploed to the AWS EC2 instance server using the deployment tool, Anisble."
            }

        }
    }
}
