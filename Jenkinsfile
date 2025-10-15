pipeline {
    agent any

    tools {
        jdk 'jdk11'      // must match Jenkins Global Tool Configuration
        maven 'maven3'   // must match Jenkins Global Tool Configuration
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                bat 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging JAR...'
                bat 'mvn package'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Run Application') {
            steps {
                echo 'Running the application...'
                bat 'java -jar target/*.jar'
            }
        }
    }

    post {
        always {
            echo "Pipeline execution finished."
        }
    }
}
