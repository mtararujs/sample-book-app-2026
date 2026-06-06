pipeline {
    agent any
    triggers{ 
        pollSCM('*/1 * * * *') 
    }
    stages {
        stage('build') {
            steps {
                script{
                    build()
                }
            }
        }
        stage('deploy-dev') {
            steps {
                script{
                    deploy("DEV")
                }
            }
        }
        stage('test-dev') {
            steps {
                script{
                    test("DEV")
                }
            }
        }
        stage('deploy-stg') {
            steps {
                script{
                    deploy("STG")
                }
            }
        }
        stage('test-stg') {
            steps {
                script{
                    test("STG")
                }
            }
        }
        stage('deploy-prd') {
            steps {
                script{
                    deploy("PRD")
                }
            }
        }
        stage('test-prd') {
            steps {
                script{
                    test("PRD")
                }
            }
        }
    }
}

def build(){
    echo "Building sample-book-app.."
    sh "ls -a"
}

def deploy(String environment){
    echo "Deployment to ${environment} environment.."
}

def test(String environment){
    echo "Testing Sample Book App service on ${environment} environment..."
}