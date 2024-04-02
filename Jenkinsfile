// Sample Jenkins file template
pipeline {
    agent {
        dockerfile true
        // node {
        //     label 'jenkins-agent'
        // }
    }

    // tools { nodejs 'node' }

    stages {
        stage('Check NodeJS configuration') {
            steps {
                sh 'npm config ls'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Lint') {
            steps {
                sh 'npm run lint'
            }
        }
        stage('Run Jest') {
            steps {
                sh 'npm test'
            }
        }
    }
    post {
        success {
            emailext(
                to: '$DEFAULT_RECIPIENTS',
                subject: "Success Pipeline: ${currentBuild.fullDisplayName}",
                body: "Everything good with ${env.BUILD_URL}"
            )
        }
        failure {
            emailext(
                to: '$DEFAULT_RECIPIENTS',
                subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                body: "Something is wrong with ${env.BUILD_URL}"
            )
        }
    }
}
