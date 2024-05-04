pipeline{
    agent any

    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests'){
            steps{
                sh 'mvn test'
                sh 'newman run collection.json'
            }

        }
        stage('Code Analysis'){
            steps{
                sh 'sonar-scanner'
            }

        }
        stage('Security Scan'){
            steps{
                sh 'zap-cli -t <target_URL>'
            }

        }
        stage('Deploy to Staging'){
            steps{
                sh 'ansible-playbook deploy-to-staging.yml'
            }

        }
        stage('Integration Tests on Staging'){
            steps{
                sh 'newman run staging-collection.json'
            }

        }
        stage('Deploy to Production'){
            steps{
                sh 'ansible-playbook deploy-to-production.yml'
            }

        }
    }
}
