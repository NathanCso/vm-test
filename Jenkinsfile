 pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                
                git branch: 'main', url: 'https://github.com/NathanCso/vm-test.git'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                
                sh 'ansible-playbook -i ansible/hosts.ini ansible/playbook.yml'
            }
        }
    }
}
