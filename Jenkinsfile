pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {
        stage('clean') {
            steps {
                bat "mvn clean"
            }
        }

        stage('install') {
            steps {
                bat "mvn install"
            }
        }

        stage('test') {
            steps {
                bat "mvn test"
            }
        }

        stage('package') {
            steps {
                bat "mvn package"
            }
        }
    }
    post {
    success {
        emailext(
            subject: "Jenkins Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Build ${env.BUILD_NUMBER} was successful.",
            to: "YOUR_GMAIL@gmail.com"
        )
    }

    failure {
        emailext(
            subject: "Jenkins Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Build ${env.BUILD_NUMBER} has failed.",
            to: "YOUR_GMAIL@gmail.com"
        )
    }
}
}
