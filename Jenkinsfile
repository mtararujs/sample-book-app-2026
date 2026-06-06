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
    sh "docker build -t mtararujs/sample-book-app ."
    
    echo "Pushing image to docker registry.."
    sh "docker push mtararujs/sample-book-app"
}

def deploy(String environment){
    echo "Deployment to ${environment} environment.."
    sh "docker pull mtararujs/sample-book-app"
    sh "docker compose down sample-book-app-${environment.toLowerCase()}"
    sh "docker compose up -d sample-book-app-${environment.toLowerCase()}"
    echo "Deployment to ${environment} environment finished.."
}

def test(String environment){
    echo "Testing Sample Book App service on ${environment} environment..."
    sh "docker pull mtararujs/api-tests"
    def directory = pwd()
    sh "echo '${directory}'"
    sh "docker run --rm --network sample-book-app-compose-network -v '${directory}'/test-reports:/api-tests/mochawesome-report mtararujs/api-tests BOOKS BOOK_ ${environment}"
    // obtain/archive report
    echo "Testing Sample Book App service on ${environment} environment finished..."
}