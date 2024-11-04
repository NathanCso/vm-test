pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                
                git 'https://github.com/NathanCso/vm-test.git'
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
