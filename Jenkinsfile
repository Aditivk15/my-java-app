pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'Maven 3.9.11'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Aditivk15/my-java-app.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Run App') {
            steps {
                bat 'java -jar target\\*.jar'
            }
        }
    }
}
