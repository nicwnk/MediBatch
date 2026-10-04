pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = 'medibatch'
        TAG = "${env.BUILD_NUMBER}"
    }

    options {
        disableConcurrentBuilds()
        buildDiscarder(logRotator(numToKeepStr: '15'))
        timeout(time: 20, unit: 'MINUTES')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                sh 'docker ps'      // proves Jenkins can reach Docker
            }
        }
        stage('Test') {
            steps { echo 'TODO: docker build --target test for each module' }
        }
        stage('Build Images') {
            steps { echo 'TODO: docker compose build' }
        }
        stage('Deploy') {
            steps { echo 'TODO: docker compose up -d --no-build --remove-orphans' }
        }
        stage('Smoke Test') {
            steps { echo 'TODO: check /health through the proxy' }
        }
    }

    post {
        success { echo "Build ${TAG} succeeded" }
        failure { echo "Build ${TAG} failed. Check the stage logs." }
    }
}