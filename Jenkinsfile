pipeline {
    agent any

    tools {
        maven 'Maven 3.8.5' // Ensure this matches your Jenkins Maven installation name
        jdk 'Java 17'       // Ensure this matches your Jenkins JDK installation name
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/abhiram165/API-Testing-Framework.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded.'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
