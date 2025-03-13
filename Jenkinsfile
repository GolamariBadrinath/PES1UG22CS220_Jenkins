pipeline {
    agent any
    
    environment {
        REPO_URL = 'https://github.com/GolamariBadrinath/PES1UG22CS220_Jenkins'
        BRANCH = 'main' // Push directly to main
        FILE_NAME = 'new_file.cpp'
        BUILD_OUTPUT = 'PES1UG22CS220-1'
        SRN = 'PES1UG22CS220'
    }

    stages {
        stage('Create & Push New .cpp File') {
            steps {
                script {
                    sh '''
                    git config user.email "golamaribadrinath@gmail.com"
                    git config user.name "GolamariBadrinath"
                    
                    # Ensure we are on the main branch
                    git checkout main
                    
                    # Create and commit the new file
                    echo '#include <iostream>\nint main() { std::cout << "Hello, Jenkins!" << std::endl; return 0; }' > ${FILE_NAME}
                    git add ${FILE_NAME}
                    git commit -m "Adding new C++ file"

                    # Push changes to the main branch
                    git push origin main
                    '''
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh "g++ ${FILE_NAME} -o ${BUILD_OUTPUT}"
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
            echo 'Pipeline failed'
        }
        success {
            echo 'Pipeline completed successfully'
        }
    }
}
