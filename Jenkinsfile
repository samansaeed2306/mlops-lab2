pipeline {
    agent any

    stages {
        stage('Cloning the repository') {
            steps {
                git 'https://github.com/samansaeed2306/mlops-lab2'
            }
        }

        stage('Installation of dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Execution of test.py') {
            steps {
                sh 'pytest test.py'
            }
        }

        stage('Deploying step') {
            steps {
                script {
                    def branchName = sh(script: 'git rev-parse --abbrev-ref HEAD', returnStdout: true).trim()
                    if (branchName == 'main') {
                        echo 'Now Deploying to production'
                    } else {
                        echo 'Now Deploying to UAT'
                    }
                }
            }
        }
    }
}
