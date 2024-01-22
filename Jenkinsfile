pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/amruthaa25/Nginx.git'
        NGINX_PATH = 'D:\\devops\\Nginx\\nginx-1.24.0\\nginx-1.24.0\\htmldocs'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Use the checkout step to clone the Git repository
                    checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/amruthaa25/Nginx.git']])
                }
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    // Using the Jenkins workspace variable to reference files
                    bat 'xcopy /y "D:\\devops\\Nginx\\Nginx_exp\\index.html" "%NGINX_PATH%"'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! You can add additional steps here.'
        }
        failure {
            echo 'Pipeline failed! You may want to take some actions.'
        }
    }
}
