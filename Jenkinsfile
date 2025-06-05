pipeline {
    agent any

    environment {
        JAVA_HOME = '/opt/homebrew/opt/openjdk@17'  // Update this path as needed
        PATH = "${env.JAVA_HOME}/bin:/opt/homebrew/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/abhiram165/API-Testing-Framework.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn -v'
                sh 'java -version'
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
            echo '✅ Build and tests succeeded.'
        }
        failure {
            echo '❌ Build or tests failed.'
        }
    }
}
