pipeline {
    agent any
    
    environment {
        REPO_URL = 'https://github.com/GolamariBadrinath/PES1UG22CS220_Jenkins'
        BRANCH = 'main' // Change this if needed
        FILE_NAME = 'new_file.cpp'
        BUILD_OUTPUT = 'PES1UG22CS220-1'
        SRN = 'PES1UG22CS220'
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    sh 'git clone ${REPO_URL} repo'
                    sh 'cd repo && git checkout ${BRANCH}'
                }
            }
        }
        
        stage('Create & Push New .cpp File') {
            steps {
                script {
                    sh '''
                    cd repo
                    echo '#include <iostream>\nint main() { std::cout << "Hello, Jenkins!" << std::endl; return 0; }' > ${FILE_NAME}
                    git add ${FILE_NAME}
                    git commit -m "Adding new C++ file"
                    git push origin ${BRANCH}
                    '''
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    sh "g++ repo/${FILE_NAME} -o ${BUILD_OUTPUT}"
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
