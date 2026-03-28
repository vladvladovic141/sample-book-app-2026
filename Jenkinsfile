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
                    deploy("DEV", 1010);
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
                    deploy("STG", 2020);
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
                    deploy("PROD", 3030);
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
def deploy(String environment, int port){
    echo "Deployment to ${environment} has started.."
    git branch: 'main', poll: false, url: 'https://github.com/vladvladovic141/sample-book-app-2026.git'
    bat "npm install"
    bat "dir"

    bat "node_modules\\.bin\\pm2 delete \"books-${environment}\" || exit 0"
    bat "node_modules\\.bin\\pm2 start -n \"books-${environment}\" index.js -- ${port}"
    echo "Deployment to ${environment} dev finished"       
}
def test(String environment){
    echo "Testing book service has started on ${environment}.."
    git branch: 'main', poll: false, url: 'https://github.com/vladvladovic141/Sample-API-automation.git'
    bat "npm install"
    bat "npm run books BOOKS_${environment}"
    echo "Testing book service finished on ${environment}."    
}