pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-23-openjdk-amd64'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Spring Boot') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
    }

    // This section replaces the "Post-build Actions" UI [cite: 43, 44]
    post {
        always {
            emailext (
                subject: "Status: ${currentBuild.fullDisplayName}",
                body: "Build ${env.BUILD_NUMBER} finished. Status: ${currentBuild.currentResult}. Check here: ${env.BUILD_URL}",
                to: 'limamahmedou2003@gmail.com' // Put your email address here [cite: 45]
            )
        }
    }
}
