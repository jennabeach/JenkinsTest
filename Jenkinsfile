pipeline {
    agent {
        docker {
            image 'maven:3.9.12-eclipse-temurin-21-alpine'
        }
    }

    stages {
        stage('Environment Info') {
            steps {
                sh 'java -version'
                sh 'mvn --version'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Starting build..."'
                sh 'mvn help:evaluate -Dexpression=maven.version -q -DforceStdout'
            }
        }

        stage('Finish') {
            steps {
                sh 'echo "Build completed successfully"'
            }
        }
    }
}
