pipeline{
    agent any

    stages{
        stage('Build'){
            steps{
                echo "mvn clean package"
            }
        }
        stage('Unit and Integration Tests'){
            steps{
                echo "mvn test"
                echo "newman run collection.json"
            }

        }
        stage('Code Analysis'){
            steps{
                echo "sonar-scanner"
            }

        }
        stage('Security Scan'){
            steps{
                echo "zap-cli -t <target_URL>"
            }

        }
        stage('Deploy to Staging'){
            steps{
                echo "ansible-playbook deploy-to-staging.yml"
            }

        }
        stage('Integration Tests on Staging'){
            steps{
                echo "newman run staging-collection.json"
            }

        }
        stage('Deploy to Production'){
            steps{
                echo "ansible-playbook deploy-to-production.yml"
            }

        }
    }
}
