pipeline{
    agent any
    tools {


    }
    environment {
        PROJECT_NAME = 'MyApp'
        DEPLOY_ENV = 'Production'
        SERVER_CREDENTIALS = credentials('server-credentials-id')
    }
    stages {
        stage('Build') {
            steps {
                echo "Building...${PROJECT_NAME} for ${DEPLOY_ENV}"
                nodejs("Node-Igor"){
                    sh "npm version"
                }
            }
        }
        stage('Test') {
            steps {
                echo "Testing...${PROJECT_NAME} for ${DEPLOY_ENV}"
            }
        }
        stage('Deploy') {
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