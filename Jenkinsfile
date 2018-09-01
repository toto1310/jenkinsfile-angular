pipeline {
    agent {
        docker {
            image 'node:8-alpine'
        }
    }
    // environment {
        // workDir = 'example/maven'
    // }

    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build --prod'
            }
        }
        stage('Lint') {
            steps {
                sh 'npm run lint'
                step([
                    $class: 'CheckStylePublisher',
                    pattern: "checkstyle-result.xml"
                ])

            }
        }
    }
}
