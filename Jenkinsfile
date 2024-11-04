pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Spécifie explicitement la branche "main" lors du clonage
                git branch: 'main', url: 'https://github.com/NathanCso/vm-test.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                // Exécuter le playbook Ansible
                sh 'ansible-playbook -i hosts.ini playbook.yml'
            }
        }
    }
}
