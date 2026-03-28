pipeline {
    agent any
    triggers {
        pollSCM('*/1 * * * *')
    }
    
    stages {
        stage('build-install-deps') {
            steps {
                echo "Installing all necessary node dependencies"
            }
        }
        stage('deploy-dev') {
            steps {
                echo "Deployment to dev has started.."
                echo "Deployment to dev finished"
            }
        }
        stage('test-dev') {
            steps {
                echo "Testing book service has started on Dev.."
                echo "Testing book service finished on Dev"
            }
        }
        stage('deploy-stg') {
            steps {
                echo "Deployment to stg has started.."
                echo "Deployment to stg finished"
            }
        }
        stage('test-stg') {
            steps {
                echo "Testing book service has started on Stg.."
                echo "Testing book service finished on Stg"
            }
        }
        stage('deploy-prod') {
            steps {
                echo "Deployment to prod has started.."
                echo "Deployment to prod finished"
            }
        }
        stage('test-prod') {
            steps {
                echo "Testing book service has started on prod.."
                echo "Testing book service finished on prod"
            }
        }
    }
}