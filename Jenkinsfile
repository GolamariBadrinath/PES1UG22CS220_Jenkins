pipeline {
    agent any
    
    environment {
        REPO_URL = 'https://github.com/GolamariBadrinath/PES1UG22CS220_Jenkins'
        BRANCH = 'main'
        CPP_FILE = 'new_invalid.cpp'  // Intentional error: Wrong filename
        BUILD_OUTPUT = 'new_program'
        SRN = 'PES1UG22CS220'
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    sh '''
                    git config user.email "golamaribadrinath@gmail.com"
                    git config user.name "GolamariBadrinath"
                    git fetch origin ${BRANCH}
                    git reset --hard origin/${BRANCH}
                    '''
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh "g++ ${CPP_FILE} -o ${BUILD_OUTPUT}"  // This should fail
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    sh "./${BUILD_OUTPUT}"
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    echo "Deploying ${SRN}..."
                    sh "echo 'Deployment simulated for ${SRN}'"
                }
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'  // Should be executed when build fails
        }
        success {
            echo 'Pipeline completed successfully'
        }
    }
}
