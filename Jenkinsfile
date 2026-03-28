pipeline {
    agent any
    triggers {
        pollSCM('*/1 * * * *')
    }

    stages {
        stage('build-install-deps') {
            steps {
                script{
                    build();
                }
            }
        }
        stage('deploy-dev') {
            steps {
                script{
                    deploy("DEV");
                }
            }
        }
        stage('test-dev') {
            steps {
                script{
                    test("DEV");
                }
            }
        }
        stage('deploy-stg') {
            steps {
                script{
                    deploy("STG");
                }
            }
        }
        stage('test-stg') {
            steps {
                script{
                    test("STG");
                }
            }
        }
        stage('deploy-prod') {
            steps {
                script{
                    deploy("PROD");
                }
            }
        }
        stage('test-prod') {
            steps {
                script{
                    test("PROD");
                }
            }
        }
    }
}

def build(){
    echo "Installing all necessary node dependencies" 
    bat "npm install"
    echo "All dependencies installed"
}
def deploy(String environment){
    echo "Deployment to ${environment} has started.."
    bat "dir"
    echo "Deployment to ${environment} dev finished"       
}
def test(String environment){
    echo "Testing book service has started on ${environment}.."
    echo "Testing book service finished on ${environment}."    
}