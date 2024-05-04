pipeline{
    agent any

    environtment {
        DIRECTORY_PATH = '/path/to/code/directory'
        TESTING_ENVIRONMENT = 'TestingEnvironment'
        PRODUCTION_ENVIRONMENT = 'Shehani'
    }
    stages{
        stage('Build'){
            steps{
                echo "fetch the source code from '${env.DIRECTORY_PATH}'"
                echo "compile the code and generate any necessary artifacts"
            }
        }
        stage('Test'){
            steps{
                echo "unit tests"
                echo "integration tests"
            }

        }
        stage('Code Quality check'){
            steps{
                echo "check the quality of the code"
            }

        }
        stage('Deploy'){
            steps{
                echo "deploy the application to '${env.TESTING_ENVIROMENT}'"
            }

        }
        stage('Approval'){
            steps{
                echo "Waiting for the manual approval..."
                script{
                    sleep(time: 10, unit: 'SECONDS')
                }
            }

        }
        stage('Deploy to Production'){
            steps{
                echo "Deploying the code to '${env.PRODUCTION_ENVIRONMENT}'"
            }

        }
    }
}