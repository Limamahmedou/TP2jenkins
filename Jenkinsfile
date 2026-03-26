pipeline {
    agent any

    // Requirements: Maven must be installed on the Jenkins agent 
    tools {
        // This 'maven' name must match the one configured in Manage Jenkins > Tools
        maven 'maven' 
    }

    environment {
        // Keeping your specific Java 23 path as requested
        JAVA_HOME = '/usr/lib/jvm/java-23-openjdk-amd64'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Step A.3: Pipeline as Code - Getting source from Git [cite: 11]
                checkout scm
            }
        }

        stage('Build Spring Boot') {
            steps {
                // Step A.1 & A.4: Building the application [cite: 8, 12]
                // Using 'mvn clean package' to create the JAR file
                sh 'mvn clean package -DskipTests'
            }
        }
    }

    // Part B: Email Notifications [cite: 13, 40]
    post {
        always {
            // Step B.3.6: Personalizing content with variables like $BUILD_STATUS and $BUILD_URL [cite: 46]
            emailext (
                subject: "Status: ${currentBuild.fullDisplayName} - ${currentBuild.currentResult}",
                body: """Build Number: ${env.BUILD_NUMBER}
                        Status: ${currentBuild.currentResult}
                        Check the logs here: ${env.BUILD_URL}""",
                to: 'limamahmedou2003@gmail.com' // Step B.3.5: Recipient address [cite: 45]
            )
        }
    }
}
