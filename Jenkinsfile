pipeline {
    agent any

    tools {
        jdk 'JDK21'                // Use exact name from Global Tool Config
        maven 'Maven 3.9.11'       // Use exact name from Global Tool Config
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Aditivk15/my-java-app.git'
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
