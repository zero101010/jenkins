pipeline{
    agent any
    environment {
        PROJECT_NAME = 'MyApp'
        DEPLOY_ENV = 'Production'
        SERVER_CREDENTIALS = credentials('server-credentials-id')
    }
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build from')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Whether to run tests')
    }
    stages {
        stage('Build') {
            steps {
                echo "Building...${PROJECT_NAME} for ${DEPLOY_ENV} from branch ${params.BRANCH_NAME}"
            }
        }
        stage('Test') {
            steps {
                echo "Testing...${PROJECT_NAME} for ${DEPLOY_ENV}"
            }
        }
        stage('Deploy') {
            when {
                expression { params.RUN_TESTS }
            }
            steps {
                echo 'Deploying...'
            }
        }
    }
    post {
        success {
            echo 'This will run only if the pipeline succeeds.'
        }
        failure {
            echo 'This will run only if the pipeline fails. Check the end'
        }
    }
}