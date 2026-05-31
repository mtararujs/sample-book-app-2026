pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo "Building sample-book-app-2026 ..."
            }
        }
        stage('deploy-dev') {
            steps {
                echo "Deployment to DEV environment ..."
            }
        }
        stage('test-dev') {
            steps {
                echo "Testing in DEV environment ..."
            }
        }
        stage('depoy-stg') {
            steps {
                echo "Deployment to STG environment ..."
            }
        }
        stage('test-stg') {
            steps {
                echo "Testing in STG environment ..."
            }
        }
        stage('deploy-prd') {
            steps {
                echo "Deployment to PRD environment ..."
            }
        }
        stage('test-prd') {
            steps {
                echo "Testing in PRD environment ..."
            }
        }
    }
}