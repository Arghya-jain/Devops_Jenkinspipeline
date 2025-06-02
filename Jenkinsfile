pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'   // Name of Maven in Global Tool Config
        jdk 'JAVA_HOME'       // Name of JDK in Global Tool Config
    }

    environment {
        PROJECT_NAME = 'cs014_cs039'
    }

    stages {
        stage('📥 Checkout Code') {
            steps {
                echo 'Cloning from GitHub...'
                git 'https://github.com/Arghya-jain/cs014_cs039.git'
            }
        }

        stage('🔍 Code Quality Check') {
            steps {
                echo 'Running Maven validate phase...'
                sh 'mvn validate'
            }
        }

        stage('⚙ Compile') {
            steps {
                echo 'Compiling the code...'
                sh 'mvn compile'
            }
        }

        stage('🧪 Unit Tests') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('📦 Package') {
            steps {
                echo 'Packaging the application...'
                sh 'mvn package'
            }
        }

        stage('📤 Archive Artifacts') {
            steps {
                echo 'Archiving built artifacts...'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "✅ Build for ${env.PROJECT_NAME} completed successfully."
        }
        failure {
            echo "❌ Build for ${env.PROJECT_NAME} failed."
        }
    }
}
