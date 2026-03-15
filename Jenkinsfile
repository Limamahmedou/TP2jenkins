pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupère automatiquement le code du dépôt GitHub lié au job [cite: 53, 55]
                checkout scm
            }
        }
        stage('Compile') {
            steps {
                script {
                    // Compile le fichier HelloWorld.java présent dans le dossier courant [cite: 62, 63]
                    sh 'javac HelloWorld.java'
                }
            }
        }
        stage('Run') {
            steps {
                script {
                    // Exécute le programme compilé en utilisant votre chemin Java 23 [cite: 70, 80]
                    sh '/usr/lib/jvm/java-23-openjdk-amd64/bin/java HelloWorld'
                }
            }
        }
    }
}
