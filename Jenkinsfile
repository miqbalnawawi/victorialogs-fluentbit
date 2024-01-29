pipeline {
    agent any

    environment {
        GITHUB_REPO_URL = "https://github.com/miqbalnawawi/victorialogs-fluentbit.git"
        BRANCH_NAME = "main"
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout([$class: 'GitSCM', branches: [[name: "${BRANCH_NAME}"]], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: "${GITHUB_REPO_URL}"]]])
                }
            }
        }

        stage('Build and Run Docker Compose') {
            steps {
                script {
                    sh 'docker-compose up -d --build'
                }
            }
        }
    }
}
