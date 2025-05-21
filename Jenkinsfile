pipeline {

    agent { label 'First' }
    
    environment {
        ENVIRONMENT = 'prod'
    }

    stages {
        stage('Preparation') {
            steps {
                echo "Current environment is: ${ENVIRONMENT}"
            }
        }

        stage('Build') {
            steps {
                echo "Building for ${ENVIRONMENT} environment..."
            }
        }

        stage('Deploy Approval') {
            when {
                expression { return env.ENVIRONMENT == 'prod' }
            }
            steps {
                script {
                    input message: "You're deploying to PRODUCTION! continue?"
                }
                echo "Deploying to production server..."
            }
        }

        stage('Post-Build') {
            steps {
                echo "Pipeline completed for ${ENVIRONMENT}"
            }
        }
    }
}