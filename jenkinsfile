

pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
    }

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Clean') {
            steps {
                bat 'mvn clean'
            }
        }

        stage('Install') {
            steps {
                bat 'mvn install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Maven Pipeline Completed Successfully!'
        }
        failure {
            echo 'Maven Pipeline Failed!'
        }
    }
}
