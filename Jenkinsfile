

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


post {
    success {
        emailext(
            subject: "SUCCESS: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
            body: """
                <h2>Build Successful!</h2>
                <p>Job: ${env.JOB_NAME}</p>
                <p>Build Number: ${env.BUILD_NUMBER}</p>
                <p>Check build: ${env.BUILD_URL}</p>
            """,
            to: 'YOUR_GMAIL@gmail.com'
        )
    }

    failure {
        emailext(
            subject: "FAILURE: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}",
            body: """
                <h2>Build Failed!</h2>
                <p>Job: ${env.JOB_NAME}</p>
                <p>Build Number: ${env.BUILD_NUMBER}</p>
                <p>Check build: ${env.BUILD_URL}</p>
            """,
            to: 'YOUR_GMAIL@gmail.com'
        )
    }
}

