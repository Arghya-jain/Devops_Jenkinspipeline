pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'
        jdk 'JAVA_HOME'
    }

    stages {
        stage('📥 Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Arghya-jain/Devops_Jenkinspipeline.git'
            }
        }

        stage('🔍 Validate') {
            steps {
                bat 'mvn validate'
               
            }
        }

        stage('⚙ Compile') {
            steps {
                bat 'mvn compile'
              
            }
        }

        stage('🧪 Test') {
            steps {
                bat 'mvn test'
               
            }
        }

        stage('📦 Package') {
            steps {
                bat 'mvn package'
                
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
