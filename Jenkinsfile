pipeline {
    agent any
    
    environment {
        SRN_VERSION = 'PES2UG22CS102'
        CPP_FILE = 'pattern.cpp'
    }
    
    stages {
        stage('Build') {
            steps {
                script {
                    try {
                        echo "Compiling ${CPP_FILE} for ${SRN_VERSION}"
                        sh 'g++ -o example.out ${CPP_FILE}'
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        throw e
                    }
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    try {
                        echo "Running tests on compiled .cpp file"
                        sh './example.out'
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        throw e
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    try {
                        echo "Deploying the application"
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        throw e
                    }
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline executed'
        }
        
        success {
            echo 'Pipeline succeeded'
        }
        
        failure {
            echo 'Pipeline failed'
        }
    }
}
