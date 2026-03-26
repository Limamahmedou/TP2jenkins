pipeline {
    agent any

    // Configuration de Maven (Prérequis) [cite: 7]
    tools {
        // Assurez-vous que le nom 'maven' correspond à celui configuré dans Jenkins > Tools
        maven 'maven' 
    }

    environment {
        // Garder votre configuration Java spécifique
        JAVA_HOME = '/usr/lib/jvm/java-23-openjdk-amd64'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Étape A.3 : Pipeline as Code - Récupération du code source [cite: 11]
                checkout scm
            }
        }
        
        stage('Build Spring Boot') {
            steps {
                // Étape A.4 : Exécuter le pipeline [cite: 12]
                // On navigue dans le bon dossier avant de lancer la commande Maven
                dir('BackEnd/JobPortal') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }
    }

    // Étape B : Notification par email [cite: 13, 40]
    post {
        always {
            // Configuration de l'action post-build "Editable Email Notification" [cite: 44]
            emailext (
                // Personnalisation du contenu avec les variables Jenkins 
                subject: "Status du Build: ${currentBuild.fullDisplayName} - ${currentBuild.currentResult}",
                body: """Numéro de Build: ${env.BUILD_NUMBER}
                        Statut: ${currentBuild.currentResult}
                        Consultez les logs détaillés ici: ${env.BUILD_URL}""",
                // Champ Destinataires [cite: 45]
                to: 'limamahmedou2003@gmail.com' 
            )
        }
    }
}
