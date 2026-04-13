pipeline {
    agent any
    environment {
        ANSIBLE_INVENTORY = '/home/ansible/TP6/inventory.inies'
        ANSIBLE_PLAYBOOK = '/home/ansible/TP6/playbook.yml'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Limamahmedou/TP2jenkins'
            }
        }
        stage('Install Ansible') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo apt-get install -y ansible'
            }
        }
        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    playbook: "${ANSIBLE_PLAYBOOK}",
                    inventory: "${ANSIBLE_INVENTORY}"
                )
            }
        }
    }
}
