pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/Anusha-Kallur/PES1UG22AM028_Jenkins.git']]
                ])
            }
        }
        stage('Build') {
            steps {
                script {
                    build 'PES1UG22AM028-1'
                    sh 'g++ main.cpp -o output'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh './output'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy'
            }
        }
    }
    post {
        failure {
            script {
                echo 'Pipeline failed'
                error 'Stopping pipeline due to failure.'
            }
        }
    }
}
