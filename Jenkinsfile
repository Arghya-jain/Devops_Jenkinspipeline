pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
        jdk 'JAVA_HOME'
    }

    stages {
        stage('📥 Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Arghya-jain/cs014_cs039.git'
            }
        }

        stage('🔍 Validate') {
            steps {
                bat 'mvn validate'
                // sh 'mvn validate'  // for Linux
            }
        }

        stage('⚙ Compile') {
            steps {
                bat 'mvn compile'
                // sh 'mvn compile'   // for Linux
            }
        }

        stage('🧪 Test') {
            steps {
                bat 'mvn test'
                // sh 'mvn test'      // for Linux
            }
        }

        stage('📦 Package') {
            steps {
                bat 'mvn package'
                // sh 'mvn package'   // for Linux
            }
        }

        stage('📤 Archive') {
            steps {
                archiveArtifacts 'target/*.jar'
            }
        }
    }

    post {
        success {
            echo '✅ Build succeeded!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
