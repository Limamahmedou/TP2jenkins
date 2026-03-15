pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupère le code depuis GitHub [cite: 55]
                // Comme vous utilisez 'Pipeline from SCM', 'checkout scm' est plus propre
                checkout scm
            }
        }
        stage('Compile') {
            steps {
                script {
                    // On se déplace dans le dossier du projet et on compile [cite: 62, 63]
                    sh 'cd /var/lib/jenkins/HelloWorldProject && javac HelloWorld.java'
                }
            }
        }
        stage('Run') {
            steps {
                script {
                    // On se déplace et on exécute avec le chemin spécifique de votre Java 23 [cite: 70]
                    sh 'cd /var/lib/jenkins/HelloWorldProject && /usr/lib/jvm/java-23-openjdk-amd64/bin/java HelloWorld'
                }
            }
        }
    }
}
