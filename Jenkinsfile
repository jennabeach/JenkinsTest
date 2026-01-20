/* Jenkinsfile for Maven build using Docker agent */
pipeline {
    agent {
        docker {
            // Use a public Maven image with Java
            image 'maven:3.9.12-eclipse-temurin-21-alpine'
            // Clean container each run
            args '-v $HOME/.m2:/root/.m2'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Running Maven build...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Maven tests...'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the project...'
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Build, test, and package succeeded!'
        }
        failure {
            echo 'Build failed. Check the logs.'
        }
    }
}
