

// pipeline {
//     agent any

//     tools {
//         maven 'MAVEN_HOME'
//     }

//     triggers {
//         githubPush()
//     }

//     stages {
//         stage('Checkout') {
//             steps {
//                 checkout scm
//             }
//         }

//         stage('Clean') {
//             steps {
//                 bat 'mvn clean'
//             }
//         }

//         stage('Install') {
//             steps {
//                 bat 'mvn install'
//             }
//         }

//         stage('Test') {
//             steps {
//                 bat 'mvn test'
//             }
//         }

//         stage('Package') {
//             steps {
//                 bat 'mvn package'
//             }
//         }
//     }

//     post {
//         success {
//             echo 'Maven Pipeline Completed Successfully!'
//         }
//         failure {
//             echo 'Maven Pipeline Failed!'
//         }
//     }
// }



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
            emailext(
                to: 'YOUR_GMAIL@gmail.com',
                subject: "SUCCESS: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                body: "Build successful! Check: ${env.BUILD_URL}"
            )
        }

        failure {
            emailext(
                to: 'abhishekreddi1006@gmail.com',
                subject: "FAILURE: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
                body: "Build failed! Check: ${env.BUILD_URL}"
            )
        }
    }
}

