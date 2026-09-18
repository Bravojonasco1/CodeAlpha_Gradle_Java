pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Java & Gradle') {
            steps {
                sh '''
                    java -version
                    ./gradlew --version
                '''
            }
        }

        stage('Test') {
            steps {
                sh './gradlew clean test'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }
}
